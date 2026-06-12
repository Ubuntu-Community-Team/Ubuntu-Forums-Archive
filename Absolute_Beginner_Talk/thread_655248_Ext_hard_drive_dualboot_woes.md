---
title: "Ext hard drive dualboot woes"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by therealtigger on 2008-01-01
Hi,

I have recently installed the newest version of ubuntu onto an external hard drive, using the live disc.
I did this because, I am using my brother's laptop which is quite slow on windows (xp) so I decided to  buy an external hard drive that I could take all my data and files with me anywhere, and also run ubuntu from it on the laptop.
The installation all went perfectly, very easy, however, now, when the hard drive is not plugged in, I cannot boot to windows anymore.
What happens is, it says "grub loading 1.5 blah blah" and then underneath that, it says "error 21". I assume this is because it cannot find grub to load, but I thought that since the hard drive wasn't plugged in, it would automatically boot to windows.
Is there anything I can do to fix it? I really don't want to leave it not working without the external hard drive plugged in, especially as it isn't my laptop.


Thanks for helping.

EDIT: ok, I think the problem might be that grub needs to be installed onto the internal hard disk (the one with windows on it) so that it can launch without the hard drive?:confused:
any ideas?
btw, I am completely new to ubuntu and linux in general, so far it seems brilliant, apart from this issue.

---

### Post by Sbarton on 2008-01-01
Sounds like a bootloader problem with windows, maybe a fixmbr will solve the problem. I noticed this post [http://ubuntuforums.org/archive/index.php/t-468572.html](http://ubuntuforums.org/archive/index.php/t-468572.html)
with similar problem, I'm sure there are other posts similar. Though the above link has 'vista' installed it may give you a clue. Scroll down the posts in that link.
Regards

---

### Post by therealtigger on 2008-01-01
Ok, I tried the fixmbr thing, and windows now boots as normal, without loading grub or anything.
However, when I press f12 at startup, and choose the ext. hard drive to boot from, it also boots straight to windows :confused: Perhaps I need to reinstall grub?

---

### Post by therealtigger on 2008-01-01
would it be a good idea for me to just start over, and use this method ([http://ubuntuforums.org/showthread.php?t=464113](http://ubuntuforums.org/showthread.php?t=464113)) 
that i just found to install it?

---

### Post by Sbarton on 2008-01-01
OK! that worked for that person. I was thinking would it be worth  reinstalling grub to the USB drive withoutt having the internal drive in. using 'SuperGrub' disc (downloadable & Free). Then installing the Main drive again and see if F12 works.
Maybe someone else has a better and quicker method rather than reinstalling Ubuntu.
regards

---

### Post by logos34 on 2008-01-01
> **therealtigger said:**
> would it be a good idea for me to just start over, and use this method ([http://ubuntuforums.org/showthread.php?t=464113](http://ubuntuforums.org/showthread.php?t=464113)) 
that i just found to install it?

all you need to do is [reinstall Grub to the usb drive mbr]("http://ubuntuforums.org/showthread.php?t=224351")...so make sure to write it to sdb or (hd1).  Then change the menu.lst 'root' lines to (hd0,0), like it says in the guide you were using

---

