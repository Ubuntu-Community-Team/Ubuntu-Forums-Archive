---
title: "Well, that doesn't work"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-09-08
Hey guys. I successfully installed Xubuntu on a hard drive. I installed it on one computer, and then I moved it to another where it was supposed to stay. Anyways, I tried running it, and it kind of started up okay. It showed Xubuntu loading up, and then the screen turned into this mess of colors and bizzare letters. It said that the GUI interface failed to start, and that some config file didn't work. I really have no idea what I can do now. Do I have to uninstall it or something? Please tell me what I can do. Thanks.

-drndrw

---

### Post by diatribe on 2007-09-08
what was the exact error message

---

### Post by Mongo5000 on 2007-09-08
im assuming that its different hardware in the new computer so your xorg.conf file is not set to that hardware

---

### Post by schorsch on 2007-09-08
Try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
at the command line. I guess you have another graphic card and another monitor attached to the new box so you have to adjust the xserver settings.

---

### Post by drndrw on 2007-09-08
> Failed to start the X server (your graphical user interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux *[my computers name, which I don't want to type]* 2.6.20-15-generic #2 SMP Sun 
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
[INDENT]Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version[/INDENT]
Module Loader present 
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational,  (WW) warning, (EE) error, (NI) Not implemented, (??) unknown.
(==) Log File: "var/log/Xorg.0.log", Time; Sat Sep 8 05:57:31 2007
(==) Using config file: "etc/X11/xorg.conf"

I did use another computer to install, so is that the problem? I also read that the computer was unable to locate RSDP. Oh, and I don't think I can get to the command line. Do you think it would be possible to rewrite the xorg.conf file?

EDIT: Wait, I ran that command and it worked. Now, am I sis, sisusb, tdfx, tga, trident, tseng or vesa? Thanks.

---

### Post by diatribe on 2007-09-08
yea, try sudo dpkg-reconfigure -phigh xserver-xorg as was stated earlier

---

### Post by schorsch on 2007-09-08
Well, if the xserver cannot start you are at the command line. Please start the command I suggested after logging in. And yes, different hardware can cause your problem.

---

### Post by drndrw on 2007-09-08
I know, I'm there. But I don't know what my X server driver is. I listed my options in my last post.

---

### Post by schorsch on 2007-09-08
I do not see any options ..... Which graphic card is in the actual machine? And you can nearly always try the vesa driver to get the GUI running.

---

### Post by drndrw on 2007-09-08
I have an ATI card in. Sorry, but I am not really sure what the specifil details are. Is there a command I can run so xorg.conf uses an ATI rather than an Nvida card?

---

### Post by annda on 2007-09-08
hi,

vesa is a generic driver. it COULD work for starters. please check your card's documentation. what is the exact make and model? if googling fot the linux x driver doesn't help you, post the name, maybe we can help find it.

---

### Post by schorsch on 2007-09-08
Do you have internet at the moment at the mentioned computer? If so, you can try
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial --ovt
startx
```

---

### Post by drndrw on 2007-09-08
If all of the drivers and what not work, then I should. I'm not sure about the exact model for the drive, but I'll figure it out. I'll give those a try. Thanks :).

---

