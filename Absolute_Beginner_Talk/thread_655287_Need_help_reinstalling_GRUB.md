---
title: "Need help reinstalling GRUB"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by rahul_s on 2008-01-01
I had Windows Vista on my HP dv6449 laptop and Ubuntu 7.04 on an ext3 partition in my external hard drive. I then installed Windows XP which overwrote the MBR to the Windows one.

I am now obviously not able to read my Ubuntu drive... Back when I was having Vista, I was also having the problem that Windows would load only if my external drive is connected. I figure the problem could be because GRUB was loaded on my external drive.

Is there a method for installing GRUB on your C drive or whenever that I can load Windows without having to connect my external drive and load Ubuntu by connecting the external hdd and selecting it from GRUB ?

I need specific advice on which drive I must load GRUB and on the commands required.

This is the  breakup of my drives
Laptop drive: 160 GB
C:   D:   E:   F:
External drive
H:   I:   ext   swap

Wish you all a happy New Year !! :)
Thanks in anticipation !! :)

---

### Post by seshomaru samma on 2008-01-01
you mean install Grub to the MBR

boot from a live Cd - ubuntu ,knoppix, whatever
open a terminal ,put 
```
grub
```
then
```
find /boot/grub/stage1
```". 
You'll get a response like "(hd0)" 
replace the question marks in the following command with whatever output you got in the last command
```
root (hd?,?)
```
then
```
setup (hd0)
```
then
```
quit
```

---

### Post by rahul_s on 2008-01-01
you said

root(hd?,?)

In my case it may return hd1, correct me if I am wrong.... what will the second '?' be ??

Also after doing this, will I be able to boot from my 1st hard drive withour connecting my external drive ?

---

### Post by nick_h on 2008-01-01
The second number is the partition number.  From what you posted I expect it will be the first partition on the second drive - (hd1,0) - but the find command is intended to check this.

---

### Post by ronmarley1 on 2008-01-01
Another option is to download and create a bootable CD of the SuperGrubDisk.  It'll find GRUB and reinstall it for you.  It's saved me a couple of times.  You can get the iso here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

EDIT:  Oops, just re-read your first post and noticed that you also have an external hard drive.  I'm not sure if SuperGrubDisk will work with this configuration.  I've only used it with the single hard drive on my laptop.  Sorry if I gave you a bum-steer!

---

### Post by rahul_s on 2008-01-01
I did the following commands after booting from the disc

sudo grub
find /boot/grub/stage1

It returned (hd1,4)

root (hd1,4)
setup (hd1)
quit

Ubuntu gets recognised
But again the problem is that I have to connect my External drive if I have to boot into Windows XP... 

:(

---

### Post by logos34 on 2008-01-01
> **rahul_s said:**
> I did the following commands after booting from the disc

sudo grub
find /boot/grub/stage1

It returned (hd1,4)

root (hd1,4)
setup (hd1)
quit

Ubuntu gets recognised
But again the problem is that I have to connect my External drive if I have to boot into Windows XP... 

:(

I thought you said you installed windows XP, replacing vista, and it overwrote grub on the internal drive's MBR?  You should be able to boot into XP by merely changing the bios hard disk boot order back so it boots the internal drive first.  The external shouldn't need to be connected for that.

---

