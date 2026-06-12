---
title: "Help With Grub Dual Boot!!"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by wtr_sprts4life on 2006-08-22
Hi to all! 

Ive just become a newbie and changed from the dark side of windows to ubuntu v. 6.06. I have to harddrives, one my master which intend to keep all my stuff on, eg windows, so i can have a dual boot. my 2nd one is partitioned 3times, one with alot of music, another one with ubuntu & swap (as install requested). it installed fine, but when i reseted the computer to boot of the hdd, it came up with a msg saying:

Grub 1.05 
Please wait...
Error 22?

can anyone help me with this, or is there a different program i should use or install so i can dual boot. I dont want to format the 2nd harddrive as i dont want to loose all my music! Help!!

Thanking anyone in advance.

PS. I no how to restore the boot record so windows works again, but i need the dual boot to work as i wanna start using ubuntu!

---

### Post by b_martinez on 2006-08-22
I'm getting dinner ready now, so i've not a lot of time. Grub needs to be on the master boot record of the hard drive you boot from. Usually the first drive. Did you install grub there? It's not really considered acceptable here to write this, but "did you google for 'grub errors'?" Search this forum for "grub re-install" and use the install disk to repair your boot. And last
'Welcome to Linux"
hth
Bill

---

### Post by b_martinez on 2006-08-22
"No Such Partition" =error 22
Here is the list address, might work as a link, i dunno
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)
Do you have the 'live' or 'desktop' cd? rescue from the live may be easier.
How to do that is not something I am sure about. I generally use the Knoppix cd.
Good luck
Bill

---

### Post by confused57 on 2006-08-22
Are you able to boot into Ubuntu on your 2nd hard drive?
If you are, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L"

If you're unable to boot Ubuntu from your hard drive, bootup with the Live CD and enter the above command.

This will show your partition tables on both hard drives.

---

### Post by confused57 on 2006-08-22
Deleted: Double post

---

### Post by confused57 on 2006-08-22
Deleted: Triple post, connection to server kept timing out when I clicked "submit", guess 3 of the submits actually made it.

---

### Post by wtr_sprts4life on 2006-08-22
thanks for you guys replies. Im at school atm, not at home, so i will try when i get home from work (after school). The cd i have is of a iso i downloaded (ubuntu 6.06) but i know its for desktop (not server etc). I cannot get the dual boot to work, however i know that ubuntu is installed on the other partitions as windows now doesnt reconize these harddrives. 

hope this gives you more info. 

JB

---

