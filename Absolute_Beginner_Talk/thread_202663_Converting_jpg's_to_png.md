---
title: "Converting jpg's to png ?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-06-23
Is there a program that will convert jpg's to png?

---

### Post by LKRaider on 2006-06-23
You can do it by simply opening the image in Gnome and selecting 'Save As...', then nameing a new file with png extension - it will be converted automatically.

If you want more control or alter the image, use the Gimp image editor.

---

### Post by nixternal on 2006-06-23
There are a bunch that do. The 2 big ones that can do them are:

1. Gimp
2. imagemagick

Both are in the repositories. If you are looking at doing a batch conversion, and are familiar with something like Irfanview, you can check out [XnView](http://www.xnview.com/)

---

### Post by IYY on 2006-06-23
If you have imagemagick installed (it might be installed by default, otherwise sudo apt-get install imagemagick):

```
convert image.jpg image.png
```

---

### Post by nitricacid on 2006-06-23
GIMP has never failed to make some of MY spectacular images.

---

### Post by aysiu on 2006-06-23
It is installed by default, and it's wonderful. You can also do them in bulk: ```
mogrify -format png *.jpg
```

---

### Post by djsroknrol on 2006-06-23
Thanks everyone...I tried to post my desktop wallpaper the otherday to a thread and the images were too big. I had jpgs up and need to convert them.

aysiu, which program is installed by default? With all the posts, I tried to man imagemagick, and mogrify and they weren't installed. 

Gimp I have now, haven't tried it yet, Gnome I tried, but didn't know I had to assign the extention to it and it would do it automaticlly....

thanks again guys....:o

---

### Post by aysiu on 2006-06-23
ImageMagick is installed by default, and it has a whole bunch of commands that go along with it (mogrify, convert, animate, etc.). You can find more info about it here: [http://www.imagemagick.org/](http://www.imagemagick.org/)

I was under the impression it was installed by default (as I don't remember having installed it manually), but you can try ```
sudo aptitude update
sudo aptitude install imagemagick
``` just to be sure.

---

### Post by FredB on 2006-06-24
It is not install by default. You have to add it by hand.

---

