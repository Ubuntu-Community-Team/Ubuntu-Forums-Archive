---
title: "xmms-skins and gxmms"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by AndreiCiprian on 2006-03-04
I have installed xmms with mp3, mp4, aac, ogg and flac support.
I have enabled the universe and multiverse repositories in synaptic.
Then a series of extra packages appeared to enhance xmms.
I have chosen xmms-skins and gxmms.
The packets were installed. 
```
dpkg -l | grep xmms
```
Here's the output.
ii  gxmms                                  0.2.1-2ubuntu2                       
ii  xmms                                   1.2.10+cvs20050209-2ubuntu2         
ii  xmms-alarm                          0.3.6
ii xmms-mp4                 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2 
ii xmms-skins                             0.5-1
> Now where are the skins and how can I use gxmms??

---

### Post by evilgold on 2006-03-04
xmms is under sound and video on the gnome applications menu. to change skins, hit ctrl+s or right click the xmms window and go to options>skin browser.

---

### Post by ubuntuuser on 2006-03-04
In the skin browser, click "Add directory" and add ```
/usr/share/xmms/Skins
```. There are the default skins you installed.
To use gxmms, right-click somewhere on the empty gnome panel, then select "Add to panel", scroll down to the multimedia section, there you'll find it.

---

### Post by Qrk on 2006-03-04
gxmms is a panel applet

You need to add it to your panel to use it.

[ATTACH]6696[/ATTACH]

---

### Post by AndreiCiprian on 2006-03-10
Thank you so much, problem is now solved. Is there global hotkey support in xmms?

---

### Post by Perfect Storm on 2006-03-10
You could also give beep-media-player a try. It's almost the same as xmms just newer and it also support GTK2 so it match your desktop.

[[img]http://www.imageviper.com/displayimage/27889/0/smallbmp.jpg[/img]](http://www.imageviper.com/displayimage/27887/0/bmp.jpg)
*[size=1]Click the screenshot to enlarge*[/size]

---

