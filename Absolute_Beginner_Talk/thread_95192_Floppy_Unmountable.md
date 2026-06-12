---
title: "Floppy Unmountable"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by amwil1024 on 2005-11-26
Please help!

I have successfully formatted my hard drive,

I have successfully set up a dual OS, Win98SE and ubuntu,

I have a floppy which contains the linux drivers required for hcf modem. The floppy was made (formatted) by Win98SE, I cannot access the internet while in ubuntu until I get this driver installed.

When I insert the floppy disk into the floppy disk drive,  it doesn't appear in ubutu desktop window, and when I try to open the floppy I get "Unmountable". (I go to the ?system? area where there is an icon of all the drivers and click on the floppy drive icon, then get the "unmountable" message)

Question: Can ubuntu recognize a floppy that was formatted byWin98SE?

Ultimately I need help in getting my modem going in Linux. I'm not sure how to get a driver downloaded while in Win OS, to Linux, and, once I get it to ubuntu, I'm not really sure how to install the driver either!

---

### Post by No-Brain on 2005-11-26
go to terminal

sudo mount /dev/fd0

Thats a zero, not an oh.

I ran into this a couple of days back.  It was a WIN98 formatted diskette, so it should work.

Roger

P.S.  There is also a disk mounting utility in Administration(?).  It seems that it wouldnt work forme thoguh, so I did it the hard way. :confused:

---

### Post by sabitha on 2005-11-26
try fix the /etc/fstab

$ sudo gedit /etc/fstab

change the line :

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

with

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

then reboot the computer

that's work for me on hoary 5.04 ;)

---

### Post by Tosa on 2005-11-28
Hi,
I've got the same problem. Floppy isn't mounted on startup. I did what you've sugested, but it didn't help. Any other suggestions?

---

