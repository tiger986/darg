## Drag and limit the boundary
#### JS code
```javascript
var dragging = false; 
var iX, iY; 
$("#drag").mousedown(function(e) { 
    dragging = true; 
    iX = e.clientX - this.offsetLeft; 
    iY = e.clientY - this.offsetTop; 
    this.setCapture && this.setCapture(); 
    return false; 
});
		
document.onmousemove = function(e) { 
    if (dragging) { 
        var e = e || window.event; 
        var oX = e.clientX - iX; 
        var oY = e.clientY - iY;
	if(oX <= 0){
	    oX = 0;
	}
	if(oX >= 700){
	    oX = 700;
	}
	if(oY <= 0){
	    oY = 0;
	}
	if(oY >= 400){
	    oY = 400;
	}
	$("#drag").css({"left":oX + "px", "top":oY + "px"}); 
	return false; 
    } 
}; 
		
$(document).mouseup(function(e) { 
    dragging = false; 
    $("#drag")[0].releaseCapture(); 
    e.cancelBubble = true; 
})
   
