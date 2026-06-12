---
title: "CSS centering and positioning"
date: 2008-11-14
forum: Art &amp; Design
---

### Post by cowboy.bebop on 2008-11-14
I basically took 2 one image and cut it in half right through the center. well im having trouble connecting them together in css and its driving me up the wall, the other part is also centering the 2 and make it look like one image. I am also not sure I am in the correct part of the forum for this so please if there is anyone out there that could help it would be appreciated =). I have also tried Google and its not finding what I need or maybe im not using the correct string. This what I have, i also put the container,div1 and div2 in the <body> and all i get is and image on top and an image on the bottom. =(

body {
		background-color: #333333;
		margin: 0;}
#container {
		width: 800px;
		margin: 0 auto;
		text-align: left;
		background-color: #6699CC;}
#div-1 {
		background-image: url(../../Portfolio/sn1.png);
		background-repeat: no-repeat;
		width: 195px;
		height: 100px;}
#div-2 {
		background-image: url(../../Portfolio/sn2.png);
		background-repeat: no-repeat;
		width: 205px;
		height: 100px;}

---

### Post by Meshach on 2008-11-14
Do you have a link I can look at?

Meshach

---

### Post by Peter76 on 2008-11-15
A div is a blockline element, which means it will always start on a new line. Set the display to inline like this:

div {
    display: inline;
}

for both div's to put them on the same line, or float them to the left.
This is what comes to mind here quickly; hope it helps..

Good luck, Peter

---

### Post by hessiess on 2008-11-15
Try positioning using absolute cordinates.

```

#div1 {
    position: absolute;
    width: 500px;
    height: 1000px;
    left: 0px;
    top: 30px;
}


#div2 {
    position: absolute;
    width: 500px;
    height: 1000px;
    left: 500px;
    top: 30px;
}
```

---

### Post by alex.rayu on 2008-11-15
You may assign absolute positioning only if you assign position:relative to the container element. Otherwise their position may end up broken in relation to the rest of the site.

---

### Post by Samhain13 on 2008-11-16
> **alex.rayu said:**
> You may assign absolute positioning only if you assign position:relative to the container element. Otherwise their position may end up broken in relation to the rest of the site.

Not necessarily. Position absolute says that the element's position does not depend on the position of its parent. So whether the parent is positioned relative, absolute or fixed, if a child element is positioned absolutely, it doesn't care-- as long as top (or bottom) and left (or right) are given.

---

### Post by SreckoMicic on 2008-11-17
> You may assign absolute positioning only if you assign position:relative to the container element. Otherwise their position may end up broken in relation to the rest of the site.

With absolute position element is out of document flow by default.

Try to use float:left on both of divs.

---

### Post by alex.rayu on 2008-11-18
Right. Floats is probably the best way to go.

---

