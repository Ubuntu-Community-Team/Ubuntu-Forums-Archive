---
title: "Explain xorg.conf"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by rdilliker on 2006-09-17
Hi,

I installed Dapper Drake a few days ago and my screen isn't filled, i.e. there is a black bar on the left side. I only have on resolution listed, 800x600. I have an nvidia geforce 6600 and installed the proprietary drivers. I found a lot of tselliot's threads and it seems I need to modify my xorg.conf file.

Does anyone have a link that explains the purpose of the xorg.conf file and all the different sections? I like to know why I'm making certain changes as opposed to just blindly trying different recommendations.

Thanks.

---

### Post by ciscosurfer on 2006-09-17
[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by bulldog on 2006-09-17
Try the wiki and make a copy before you alter anything.

Can't you adjust your resolution in

preferences-->screenresolution ??

---

### Post by rdilliker on 2006-09-17
Thanks for the replies guys. I was stupid and only searched the unbuntuforums. A google search turned up good explanations of Xorg. 

I only have an option for 800x600 in preferences.

---

### Post by fragos on 2006-09-17
Open up a terminal window and run the following command:

sudo dpkg-reconfigure xserver-xorg

This is a text based application with explanations of each step.  follow them carefully.  If your unsure what to use at a prompt, select the default offered.  For some of these prompts the default is a blank field.  You will be given a chance to select the resolutions you wish to support.

The only downside is that it will select the "nv" 2D nvidia driver instead of the 3D you installed.  Befor proceeding, run:

gksudo gedit /etc/X11/xorg.conf

Find where "nv" was used and change it to "nvidia"

---

### Post by comppsyco on 2006-09-17
Are you sure that you don't need to change the firmware settings on your moniter? That may be the issue.

---

### Post by bodhi.zazen on 2006-09-17
To configure X use:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It is shorter.

Then re-start X -> 3 finger salute -> Ctrl-Alt-Backspace

If that does not work, 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

monitor and post xorg.ocnf.

---

