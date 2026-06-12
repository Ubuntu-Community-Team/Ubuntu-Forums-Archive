---
title: "Changing resolution"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by HyperX on 2006-01-10
When I setup ubuntu, I selected the 5 or 6 resolutions that I knew my vid card can support. However, when I got into the GUI, i noticed I could go one up, 1280x1024 - right now i am one below that in my selection of video mode in the GUI. What text file do I need to edit to add the 1280x1024 resolution? 

Thanks!!

---

### Post by kaamos on 2006-01-10
You can edit the file with this command
```
sudo gedit /etc/X11/xorg.conf
```
The part about resolutions is pretty self explanatory. Ask if you have any problems.

---

### Post by HyperX on 2006-01-10
[QUOTE=kaamos]You can edit the file with this command
```
sudo gedit /etc/X11/xorg.conf
```
The part about resolutions is pretty self explanatory. Ask if you have any problems.[/QUOTE]


Thanks much!

---

### Post by patrick295767 on 2006-01-11
```
sudo dpkg-reconfigure xserver-xorg
```

Greetz

---

