---
title: "Noob in need of Ubuntu help (usb related)"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by kingleer on 2008-02-08
I accidentally disabled usb2.0.

By typing the following in the terminal 

> 

sudo modprobe -r ehci_hcd

Test if the copy/write process is stable, and if you want to disable USB 2.0 upon boot, type:

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r`


I would now like to reverse this, because USB 1 is slow as hell.

---

### Post by Pelham123 on 2008-02-09
Patience....

[http://ubuntuforums.org/showthread.php?t=691502](http://ubuntuforums.org/showthread.php?t=691502)

And perseverance...

[http://ubuntuforums.org/newreply.php?do=newreply&p=3991125&](http://ubuntuforums.org/newreply.php?do=newreply&p=3991125&)

---

