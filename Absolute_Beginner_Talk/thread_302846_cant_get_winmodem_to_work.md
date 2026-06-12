---
title: "cant get winmodem to work"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by s1baker on 2006-11-19
I have ubuntu 6.06 LTS kernel 2.6.15-26-386
installed on a AMD 64 athlon with the ubuntu !386 install.

My winmodem chip is a Genica PC Tel 56K v.92 modem with a
Silicon Laborities Intel 537 chip, Vendor ID 1543.

I downloaded a driver I thought would work: intel 537 V9x DF
modem Linuxdriver ( intel-537EP-2.60.80.0-mdk10-smp)
but when I run the make 537 compilar
command I get this error message:

 /boot/vmlinuz.autoconf.h: no such file or directory 
 /boot/vmlinuz.version.h:  no such file or directory

Can a winmodem work on ubuntu 6.06 LTS or do I need to get a different modem?

---

### Post by ReaderRat on 2006-11-19
Are you sure you are in the right directory when you try to "make". You need to be in the same directory as the files you are working with.

Also, this may help:
[**Modem HowTo**](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by lalaland on 2006-11-19
That looks like a binary driver for Mandrake.... wont help much
try Linmodems website for some tips, also [http://ubuntuforums.org/showthread.php?t=155170l](http://ubuntuforums.org/showthread.php?t=155170l)

---

