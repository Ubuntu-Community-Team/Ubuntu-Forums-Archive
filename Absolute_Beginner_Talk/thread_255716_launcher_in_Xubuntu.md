---
title: "launcher in Xubuntu"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-09-11
Hi, I use Ubuntu in the Office and I know how to create launcher (shortcut) on the desktop. I have Xubuntu at home and I could not figure out how to make a shortcut on dsktop. Can someone help me about this? Thanks in advance.

---

### Post by Najand on 2006-09-11
I don't knwo much about xubuntu, but I think symbolic links works as lauchers in X. To make a symbolic Link you can use this command in Terminal:
```

sudo ln -s <FILENAME> <LINKNAME>

```
If you change the <LINKNAME> to "~/Desktop", you can have it on the desktop... 
[COLOR="Red"]Caution[/COLOR] You need to write the Filename, completely from the root filesystem to the place the file is.

---

### Post by MetalMusicAddict on 2006-09-11
Its kinda weird but heres how I do it.

Create a file in mousepad and call it Whateverapp**.desktop**

Inside should look something like this:

This is for my Quake4.desktop file
```

[Desktop Entry]
Encoding=UFT-8
Name=Quake 4
Comment=FPS
Exec=quake4 +set s_driver oss
Icon=/home/atm/Icons/quake4.png
Terminal=false
StartupNotify=true
Type=Application
```

Thats basically the format. Edit to suit.

---

### Post by Sp00ne on 2006-09-11
A shortcut to what, exactly?

---

