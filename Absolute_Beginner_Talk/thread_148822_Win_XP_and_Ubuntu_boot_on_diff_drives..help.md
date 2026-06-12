---
title: "Win XP and Ubuntu boot on diff drives..help"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by kbrown3074 on 2006-03-22
I have windows XP on my slave drive, and ubuntu as my master drive.  I have grub installed.  My grub menu does not take me to windows.  I have the drive mounted as read only and on hdb5 using diskmounter.  Could this be what is going wrong?  If so, how do I fix?  If it is correct, what should my grub menu item be..its below

title         Windows XP
root          (hd1,4)
makeactive
chainloader   +1

---

### Post by aysiu on 2006-03-22
I don't know for certain, but I think Windows like to be the master with Linux the slave.

I'm not speaking metaphorically here--I mean in terms of slave and master hard drives.

---

### Post by kbrown3074 on 2006-03-22
Ok..so if I switch the two..what about GRUB?  Do I have to do anything to get it to work?

It appears the way it is now, that the MRB is messed up.  How can I fix the MBR thru Ubuntu??

---

### Post by Mark_in_Hollywood on 2006-03-22
Once you have the cable end on the XP drive, boot in safe mode and do:

fdisk ?

Follow the help screen to fix the MBR

---

### Post by confused57 on 2006-03-22
This thread may help, worked for me:

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

---

### Post by aysiu on 2006-03-22
[QUOTE=kbrown3074]Ok..so if I switch the two..what about GRUB?  Do I have to do anything to get it to work?

It appears the way it is now, that the MRB is messed up.  How can I fix the MBR thru Ubuntu??[/QUOTE] If you switched them, you'd reinstall Grub:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by kbrown3074 on 2006-03-22
well..I tried the other thread and now Im getting  'disk does not exist' error when I try booting up XP.

I guess I can try switching the master/slave around and see if that works.  If that does not work..what next??

---

