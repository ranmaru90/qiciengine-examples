# rightMiddle

* 实例演示recttransform中right-middle右侧居中模式。效果图如下：<br>
![rightMiddle](images\UI.png)

## UI

* 在新建场景中创建一个UIImage作为RightMiddle1，设置节点的大小为资源图片的原始大小，并设置右侧居中模式，如下图：<br>
![](images\right.png)
* 创建脚本UI.js，负责动态状态一个UIImage作为leftMiddle2，并设置右侧居中模式。脚本挂在根节点下。<br>
代码如下：<br>

```javascript
/**
 * Anchored the Node to Left-Bottom
 */ 
var UI = qc.defineBehaviour('qc.engine.UI', qc.Behaviour, function() {
}, {
    // fields need to serialize
});

UI.prototype.awake = function() {
	// Download the texture and then create UIImage
    var self = this;
    self.game.assets.load('texture2', 'Assets/texture/texture2.bin', function(t) {
        // create UIImage
        var node = self.game.add.image(self.gameObject);
        node.name = 'LeftMiddle2';
        node.texture = t;
        
        // set minAnchor and maxAnchor
        // 0: left/top
        // 1: right/bottom
        node.setAnchor(new qc.Point(1, 0.5), new qc.Point(1, 0.5));
        
        // The Node's center is Right-Middle
        node.pivotX = 1;
        node.pivotY = 0.5;
        
        // set the position
        node.anchoredX = -100;
        node.anchoredY = 100;
        
        // set size
        node.resetNativeSize();
    });
};

```