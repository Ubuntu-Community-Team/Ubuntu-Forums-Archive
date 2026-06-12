---
title: "[SOLVED] Gutsy won't even boot"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by ByKeLaO on 2007-12-16
After giving up on trying to get feisty working at any respectable speed, I decided to get gutsy instead.

Setup
-----
sda -> 80GB IDE Disk with ubuntu installed
sdb -> 320GB SATA Disk with Vista installed

sdb is my boot disk (should be called sda, shouldn't it?)

I used EasyBCD and NeoGrub to set up a dual boot with vista and ubuntu. Now when I boot up it lets me choose between vista and ubuntu. Vista boots fine, but when I select Ubuntu (and thus enter neogrub bootloader) none of the options work. They all give error 17. What's wrong?

This is getting really annoying. I've been trying to set up ubuntu for about 6 hours now. If nobody can help me, I will give up on Ubuntu and use some other distro instead.

---

### Post by Pumalite on 2007-12-16
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by deepank on 2007-12-16
> sdb is my boot disk (should be called sda, shouldn't it?)
You are installing Vista on some other hard disk than Ubuntu. So computer recognises your first hard disk as sda and second as sdab. 

I think you must check your partition entries in the grub. Installing another distro won't help in your case I think as you will encounter the same error if your boot entries are wrong.

---

### Post by Pumalite on 2007-12-16
I agree. Vista should be in sda.

---

### Post by ByKeLaO on 2007-12-16
Here's a status report.

Inside of windows, Drive 0 is my linux drive and Drive 1 is my vista drive.
Inside of the GRUB bootloader, Drive 0 is vista and Drive 1 is linux.
See the problem?

Since I can't boot into Linux, I can't change the menu.lst file, so I can't boot into linux. (woo, a circular reference)

Any ideas about how to change my menu.lst to replace instances of hd0 with hd1 (like a find-replace)?

---

### Post by ByKeLaO on 2007-12-16
OK I managed to fix it. I booted back onto the live CD and ran:
```
sudo gedit
```
Opened up menu.lst, and replaced hd0 with hd1 and vice versa. Now it works like a charm!
Just gotta get wireless networking up and running now... Anyone know how to install the rt23 driver for my belkin wireless g usb network adapter?

---

