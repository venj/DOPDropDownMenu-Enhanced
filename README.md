# DOPDropDownMenu-Enhanced
DOPDropDownMenu 添加双列表 优化版 （double tableView, The optimization version ）

首先 感谢 DOPDropDownMenu 作者的无私奉献和允许,  https://github.com/dopcn/DOPDropDownMenu 

我在此基础上美化来了界面，添加了双列表的应用，优化了代码，增强了稳定性，希望大家喜欢

First, I would like to thank the author of the [DOPDropDownMenu](https://github.com/dopcn/DOPDropDownMenu) for their selfless dedication.

This enhanced version includes beautiful improvements to the interface, double tableview capability, optimized code, and improved stability.  Enjoy!

### 应用截图

![image](https://raw.githubusercontent.com/12207480/DOPDropDownMenu-Enhanced/master/screenshot/dopmendemo.gif)

### 用法

```objc
#pragma mark - data source protocol
@class DOPDropDownMenu;

@protocol DOPDropDownMenuDataSource <NSObject>

@required

/**
 *  返回 menu 第column列有多少行
 */
- (NSInteger)menu:(DOPDropDownMenu *)menu numberOfRowsInColumn:(NSInteger)column;

/**
 *  返回 menu 第column列 每行title
 */
- (NSString *)menu:(DOPDropDownMenu *)menu titleForRowAtIndexPath:(DOPIndexPath *)indexPath;

@optional
/**
 *  返回 menu 有多少列 ，默认1列
 */
- (NSInteger)numberOfColumnsInMenu:(DOPDropDownMenu *)menu;


/** 新增
 *  当有column列 row 行 返回有多少个item ，如果>0，说明有二级列表 ，=0 没有二级列表
 *  如果都没有可以不实现该协议
 */
- (NSInteger)menu:(DOPDropDownMenu *)menu numberOfItemsInRow:(NSInteger)row column:(NSInteger)column;

/** 新增
 *  当有column列 row 行 item项 title
 *  如果都没有可以不实现该协议
 */
- (NSString *)menu:(DOPDropDownMenu *)menu titleForItemsInRowAtIndexPath:(DOPIndexPath *)indexPath;
@end

#pragma mark - delegate
@protocol DOPDropDownMenuDelegate <NSObject>
@optional
/**
 *  点击代理，点击了第column 第row 或者item项，如果 item >=0
 */
- (void)menu:(DOPDropDownMenu *)menu didSelectRowAtIndexPath:(DOPIndexPath *)indexPath;
@end
```

# 本Fork加入的功能

1. 增加了`placeholderMenuTitles`属性，用于在各数据项为空的情况下，显示一个可用的占位菜单；
2. 增加了`reloadData`，能够动态加载菜单项目；
3. 现在菜单数量也可以动态加载了；
4. 去掉了图片引用，原项目中的图片被替换为由贝塞尔曲线生成的图片；
5. 菜单列表继续拉动时不再显示的分隔符；
6. 将菜单标题的三角指示左移了5pt。
7. 修正了某些并不长的菜单标题显示为“...”的问题。
8. 增加了隐藏展开的菜单的方法。
9. 增加了通过`indexPath`设定菜单标题的方法。

## 可能存在的问题

- `placeholderMenuTitles`和`datasource`配合的可能还不太好；
