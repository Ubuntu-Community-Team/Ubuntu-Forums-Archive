---
title: "Application Shutdown"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by aspasia82 on 2007-08-22
I've just started with Ubuntu.  I've downloaded a few widely used programs (Azureus, VLC, XChat) and I have the same problem.  As soon as I try to open a file with one of these applications (or connect to a server in the case of XChat) it shuts down.  I could download alternative programs, but there seems to be a pervasive problem here... Can anyone help?

---

### Post by kerry_s on 2007-08-22
specs?

---

### Post by aspasia82 on 2007-08-22
isp 1420 running fiesty

---

### Post by aspasia82 on 2007-08-22
inspiron 1420, rather

---

### Post by kerry_s on 2007-08-22
that's great now i know it's a dell, do you really expect every one to look it up just to help you? your providing almost no info for anyone to work with. come on.

example of what we see:
[http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420?c=us&cs=19&l=en&s=dhs)

is it stock or is it custom?

---

### Post by kerry_s on 2007-08-23
i think it's most likely your graphics card is not setup.

**press alt+f2 type> gedit /etc/X11/xorg.conf**

right click select all and middle click to paste here.

---

### Post by aspasia82 on 2007-08-23
Sorry I'm new to this.
It's pretty much off the shelf
Intel Core 2 Duo T5250, 1.5GHz, 667Mhz, 2M L2 Cache
2GB, DDR2, 667MHz 2 Dimm 
160G 5400RPM SATA Hard Drive

---

### Post by aspasia82 on 2007-08-23
Home conf file is empty.

---

### Post by kerry_s on 2007-08-23
> **aspasia82 said:**
> Home conf file is empty.

no, my instructions include nothing about home. (for future reference, open home>press> ctrl+h ,surprise it's not empty those are your other settings)

now>

**press alt+f2 type> gedit /etc/X11/xorg.conf**

---

### Post by aspasia82 on 2007-08-23
Sorry that was just a typo.  /etc/X11/xorg.conf is empty.

---

### Post by kerry_s on 2007-08-23
> **aspasia82 said:**
> Sorry that was just a typo.  /etc/X11/xorg.conf is empty.

that's not good, you sure you typed it right?

okay, that's get that set up

**press alt+f2 type> gnome-terminal**

in the terminal put this->

**sudo dpkg-reconfigure -phigh xserver-xorg**

enter you password

after that's done, logout and press> ctrl+alt+backspace <this will restart X, hopefully you selected the right driver for your vid card. good luck

---

