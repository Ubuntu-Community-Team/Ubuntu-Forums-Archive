---
title: "Converting a bunch of PNG files into GIF - any fast solution?"
date: 2007-08-18
forum: Art &amp; Design
---

### Post by Fireblend on 2007-08-18
As the title implies, I've got to convert about 50 files into GIF but don't want to spend all afternoon opening one after one; there must be some easy way I'm sure. Can anyone help? Maybe GIMP can do it?

Thanks in advance!

---

### Post by crimesaucer on 2007-08-18
I think there are commands that can do that for you.

Read through this: [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)


And as for another possible way to do it, maybe this would work, it's how I change a folder of .svg images to .png images all at once. What I'm going to do, is to just change the code for .svg to .png and .png to .gif....

And you would also need to install the Inkscape app...plus this page is for the commands: [http://www.inkscape.org/doc/inkscape-man.html](http://www.inkscape.org/doc/inkscape-man.html)

This is the code I use for changing bulk .svg images:

...first change directory to your terminal to the folder of the images...

then for .svg to .png, do this:

```
for i in *.svg; do inkscape -f "$i" -e "$i.png" -w24 -h24; done
```

-w and -h is width and height...

...so maybe this might work for .png to .gif?:

```
for i in *.png; do inkscape -f "$i" -e "$i.gif" -w24 -h24; done
```


Then, I use my Bulk Rename app with the Search and Replace option to edit all the names at once.

---

### Post by crimesaucer on 2007-08-18
Yeah, if you install Inkscape and do this code, it works:

```
for i in *.png; do inkscape -f "$i" -e "$i.gif"; done
```


It will change them to .gif, and put them in to your same folder and they will be labeled like this:

yourphoto.png.gif       GIF image


...then in Bulk Rename, set it for  Search & Replace:

Search__For: _____    .png.gif

Replace_With: _____    .gif


....then add all of you files at once and then click-->--Rename Files


that should do it, then just delete or move the .png files.

---

### Post by King_Critter on 2007-08-18
I would use ImageMagic -- simple and powerful.

---

