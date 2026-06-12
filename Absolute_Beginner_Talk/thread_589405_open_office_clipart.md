---
title: "open office clipart"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-10-24
morning all.
ok i use open office, and while i was looking through add/remove programs i noticed there was a clipart package for open office, so i thought id install it, but i can find it now that i have installed it.
i thought there might be someting in open office you could click to get it up, but i couldnt find anything, so does it just get installed to a folder like usr/share/pixmaps for example and its a case of navigating to that file when youve got office open ?
cheers

seek and ye shall find is the moral here :)

---

### Post by forestpixie on 2007-10-24
as far as I know that's the way to do it - mine are here -

/usr/share/openclipart

---

### Post by htor on 2007-10-25
It's worth nothing, OO doesn't support SVG. 
It's like car without wheels.

---

### Post by maca22 on 2008-04-13
Try the Openclipart-png package.

As of 7.1 it is automatically installed if you do a:
```
apt-get install openclipart
```

Also the following page:
[https://help.ubuntu.com/community/ClipArt](https://help.ubuntu.com/community/ClipArt)

Recommends:
```
sudo ln -s /usr/share/openclipart/png/ /usr/lib/openoffice/share/gallery/clipart
```
which creates a link from the OpenOffice clipart directory to the Openclipart install directory.

---

