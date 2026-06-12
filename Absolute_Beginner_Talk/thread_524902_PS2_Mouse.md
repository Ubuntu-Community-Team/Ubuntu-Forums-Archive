---
title: "PS/2 Mouse"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by giles.wheatley on 2007-08-13
Hi,

I am having a problem with a new installation of Feisty where it does not recognise my PS/2 mouse.  I recollect this issue from these lists before but cannot find the thread. There was a fix involving editing /etc/modules and  /etc/X11/xorg.conf  That thread also gave commands that picked up changes to these files without having to reboot. Any pointers or advice welcome.

Giles

---

### Post by philinux on 2007-08-13
You probably need to run

sudo dpkg-reconfigure -phigh xserver-xorg

Mostly click ok (enter) to auto detect, some are message screens where pressing enter dont work in those cases just press escape to continue with process.

---

### Post by giles.wheatley on 2007-08-14
Hi,

Tried that but it didn't work. I have also tried another mouse and that did not work either. Any other suggestions?

Giles

---

### Post by giles.wheatley on 2007-08-17
Many thanks
I resorted to buying a USB mouse and am now up and running
Giles

---

### Post by ugm6hr on 2007-08-17
I have seen this before in other threads.  I gather that it has been fixed with an update - so if you run the Ubuntu updates, then hopefully your PS2 mouse should work (if you still want to use it).

---

### Post by giles.wheatley on 2007-08-19
Thanks, once I have the network card working I will update and test.
Giles

---

### Post by ugm6hr on 2007-08-20
Found one of the other threads:
[http://ubuntuforums.org/showthread.php?t=514892&page=2](http://ubuntuforums.org/showthread.php?t=514892&page=2)

---

### Post by Newhere on 2007-08-20
Hello

Does anyone know if this mouse problem only affects Xbuntu of if it is present in all versions?

I am downloading the standard 7.04 desktop iso at the moment and hope to use it as a live CD for rescue/emergecy jobs so I assume that I wouldn't be able to do the updates that other people have used to get it working?

I don't have a USB mouse for testing as my good PS2 model was OK I kept it onto my new PC.

Hope this maks some sence

---

