---
title: "Can't Log Into Ubuntu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Covalent Bond on 2008-01-10
Due to a failed attempt to fix a problem with CUPSYS, I have managed to bollix Ubuntu to the point I can not log on to Ubuntu.  Have dual boot, and am writing via XP.  When I try recovery mode with either the first or second Ubuntu selection I get a black screen with writing that scrolls too fast to read, but the last stage says something about Busy Box and INITRAMFS with a blinking cursor.  When I try to log on via the first Ubuntu selection, I get a blank screen.  When I try to log on via the second Ubuntu selection, I get the Ubuntu logo, but nothing further.  I tried a clean install, but the partition selections did not match the size of the current Ubuntu partition.  My current plan is to wipe the entire disk and start over, but wanted to try the forum first to see if there is a less draconian method.  Any suggestion needs to be very elementary; wiping the disk is something I can do easily, but hate to squander the time needed.
CB

---

### Post by eolson on 2008-01-10
If you have someway of getting on the net,  download a copy of supergrub

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Covalent Bond on 2008-01-10
Thanks for the suggestion, but it is fraught with problems since I have no program to burn an ISO file as I used XP sparingly.  I seem to be left with either wiping the disk clean or ignoring Ubuntu and using XP solely.  The sloth in me is leaning to just using XP
Thanks
CB

---

### Post by houstonbofh on 2008-01-10
This is a bit complex....

Boot the Ubuntu LiveCD.  Open a terminal...
```
~$ cd /media
/media$ sudo mkdir repair
/media$ sudo mount /dev/sda1 /media/repair
```

You will now have your filesystem mounted.  You can wander in the command line or in a file browser, but only as root for changes.

For cli,
sudo -i

For GUI,
sudo nautilus

This will allow you to see what you did and compare it to a known working system. (The Live environment)

If you did not follow this, [SIZE="6"]Do Not Do It![/SIZE]  It can seriously bork your system.  However, your system is borked now so you have less to loose.

---

### Post by oldos2er on 2008-01-10
To install Ubuntu into a partition that already exists, I think you'll need to choose manual installation. Then you should be able to point it to the proper partition.

---

### Post by Covalent Bond on 2008-01-10
Houstonbofh & Oldos2er:

THANKS  for the advise; given my tiny mind, I think I will opt for the manual partition process.  I simply do not have any inkling of how to recognize what is good or bad in the system.
CB

---

