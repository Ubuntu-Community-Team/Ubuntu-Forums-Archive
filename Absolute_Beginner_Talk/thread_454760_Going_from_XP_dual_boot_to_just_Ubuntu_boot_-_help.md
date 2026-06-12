---
title: "Going from XP dual boot to just Ubuntu boot - help?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by ticopelp on 2007-05-25
Hey, everyone. I have two HDs on my machine, one with XP and one with Ubuntu. The XP drive was there first, and I installed a second HD and put Ubuntu on it. 

I want to disconnect my Windows drive and just use Ubuntu, but here's the thing. The Windows HD is set to master and Ubuntu as slave, and changing the Ubuntu HD to be the primary boot in the BIOS just results in a blank screen. The Ubuntu drive doesn't appear to be bootable on its own for some reason. 

I'm assuming this has something to do with Grub, but I don't know enough about Grub to mess with it without further advice. Do I need to edit a file? Swap the Ubuntu HD into the master position on the MB (or does that make any difference)? 

Any help much appreciated.

---

### Post by cypherzero on 2007-05-25
Your GRUB setup files might be on your XP drive, in which case you'll have to move them

$ grub-install --help

should provide info on how to do this.

If not then you'll have to look at 'devices' in your GRUB setup files, also take a peek at menu.lst.
Renumber them if you have to, I have a similar problem since I have two external USB drives and the order of all my drives keeps changing depending on whether the second drive is on or not (I just have to remember to turn it on post-startup). Reconfiguring by BIOS didn't help at all since it only has one slot for all external drives.

---

### Post by confused57 on 2007-05-25
> **ticopelp said:**
> Hey, everyone. I have two HDs on my machine, one with XP and one with Ubuntu. The XP drive was there first, and I installed a second HD and put Ubuntu on it. 

I want to disconnect my Windows drive and just use Ubuntu, but here's the thing. The Windows HD is set to master and Ubuntu as slave, and changing the Ubuntu HD to be the primary boot in the BIOS just results in a blank screen. The Ubuntu drive doesn't appear to be bootable on its own for some reason. 

I'm assuming this has something to do with Grub, but I don't know enough about Grub to mess with it without further advice. Do I need to edit a file? Swap the Ubuntu HD into the master position on the MB (or does that make any difference)? 

Any help much appreciated.
If you were booting first to your Window's drive, you need to install grub to the Ubuntu drive, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You'll probably need to do this with both drives connected, I'm not sure.  Once you have grub installed to the Ubuntu drive's mbr, then connect your Ubuntu drive as master.  When you boot, you should get a grub boot menu, if you do, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...IF it works, this change is temporary, but can be made permanent.

---

### Post by init1 on 2007-05-25
Yes, it appears to be a grub issue. 
Try
```
grub-install /dev/yourhdhere
```
and grub should install to your correct HD
yourhdhere represents the identifier of your HD
Just ask me if you need help with that

---

### Post by ticopelp on 2007-05-25
OK, I followed the instructions given by confused57, changed the Ubuntu disk to master, rebooted, and now I get Error 17: Cannot mount disk. 

Any suggestions now? :)

Edit: Err, I didn't follow the instructions to the end. Pardon my momentary burst of idiocy. Just a minute.

---

### Post by ticopelp on 2007-05-25
Okay! I've successfully booted into the Ubuntu partition. THANK YOU to everyone who posted advice in this thread, it's much appreciated.

---

### Post by confused57 on 2007-05-25
> **ticopelp said:**
> Okay! I've successfully booted into the Ubuntu partition. THANK YOU to everyone who posted advice in this thread, it's much appreciated.

Glad it worked, thought it would...edit your /boot/grub/menu.lst & make sure to change your groot line:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by ticopelp on 2007-05-25
> **confused57 said:**
> Glad it worked, thought it would...edit your /boot/grub/menu.lst & make sure to change your groot line:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

I will do that now -- thank you again!

---

