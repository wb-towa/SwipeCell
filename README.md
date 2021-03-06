# SwipeCell

SwipeCell 是一个用Swift 5.3开发的 SwiftUI库.目标是为了实现类似iOS Mail程序实现的左右滑动菜单功能.
SwipeCell可以运行在iOS13及以上版本

![Demo](Image/demo.gif)

## 按钮配置
```swift
let button1 = SwipeCellButton(buttonStyle: .titleAndImage,
                title: "Mark", 
                systemImage: "bookmark",
                titleColor: .white, 
                imageColor: .white, 
                view: nil,   
                backgroundColor: .green,
                action: {bookmark.toggle()},
                feedback:true
                )
```

```swift
//你可以将按钮设置成任意View从而实现更复杂的设计以及动态效果
let button3 = SwipeCellButton(buttonStyle: .view, title:"",systemImage: "", view: {
    AnyView(
        Group{
            if unread {
                Image(systemName: "envelope.badge")
                    .foregroundColor(.white)
                    .font(.title)
            }
            else {
                Image(systemName: "envelope.open")
                    .foregroundColor(.white)
                    .font(.title)
            }
        }
    )
}, backgroundColor: .orange, action: {unread.toggle()}, feedback: false)
```

## Slot配置
```swift
let slot1 = SwipeCellSlot(slots: [button2,button1])
let slot2 = SwipeCellSlot(slots: [button4], slotStyle: .destructive, buttonWidth: 60) //销毁模式
```

## 装配
```swift
cellView()
    .swipeCell(cellPosition: .left, leftSlot: slot4, rightSlot: nil)
```
*更多的配置选项*
```swift
cellView()
    .swipeCell(cellPosition: .both, 
                leftSlot: slot1, 
                rightSlot: slot1 ,
                swipeCellStyle: SwipeCellStyle(
                            alignment: .leading,
                            dismissWidth: 20,
                            appearWidth: 20,
                            destructiveWidth: 240, 
                            vibrationForButton: .error, 
                            vibrationForDestructive: .heavy, 
                            autoResetTime: 3)
                            )
```

## 滚动列表自动消除
```swift
  List{
     ```
  }
  .dismissSwipeCell()
}
```
* dismissSwipeCell 在editmode下支持选择,但响应较慢
* dismissSwipeCellFast 在editmode下选择cell有问题,但响应迅速
* dismissSwipeCellForScrollView 用于ScrollView

由于SwiftUI没有很好的方案能够获取滚动状态,所以采用了 [Introspect](https://github.com/siteline/SwiftUI-Introspect.git)实现的上述功能.



下载[Demo](https://github.com/fatbobman/SwipeCellDemo.git)

## 当前问题
* 动画细节仍然不足
* 滚动列表自动消除Button的实现还不完全
* EditMode模式下仍有不足


## 欢迎多提宝贵意见


