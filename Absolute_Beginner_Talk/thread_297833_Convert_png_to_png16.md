---
title: "Convert png to png16"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-11-11
This should be pretty easy to do, however I don't see an option to save an image as PNG and 16 colors only (in GIMP).

Kind of lazy to look around more... getting spoiled by the fast Ubuntu community!

---

### Post by Peepsalot on 2006-11-11
Go to Image -> Mode -> indexed -> Generate Optimum pallete
Set # of colors to 16 and hit ok, then save as png.

I think this does what you want.

---

### Post by Dual Cortex on 2006-11-11
Great, thanks!

---

### Post by Peepsalot on 2006-11-11
Also you might want to check out the "convert" command.
[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

```
convert source.jpg -colors 16 destination.png
```
I'm not sure what package it is in, but it was already on my computer.

---

### Post by IYY on 2006-11-11
It's the imagemagick package, and I think it's installed by default. :)

---

