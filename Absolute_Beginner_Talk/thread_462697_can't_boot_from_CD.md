---
title: "can't boot from CD"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Sabertootham on 2007-06-03
I have an inspiron 8100.  I have the hard drive set up into two 18GB partitions.  One has Win2K loaded, NTFS, and the other is using a Fat32.  The CD drive is first in the boot order.  I burned ubuntu FF 7.04 iso  file to a cd and verified the file using MD5.  But no matter how many times I try the laptop won't boot from the cd.  If I put a windows OS disk in the drive it boots from the disk without any trouble.  I tried booting from other computers and have the same problem.  Whats with these iso image files.  I even went as far as extracting the actual files from the iso image and nothing.  Then I bought an Ubuntu DVD and every computer will take this and boot from the cd.  Unfortunately the inspiron 8100 can't read DVD's.  What am i doing wrong?

---

### Post by N8K99 on 2007-06-03
you could try to use an alternate install cd- it doesn't have the pretty graphical installation method from within the LiveCD environment, but it does do a really good job in situations where it is, erm, somewhat difficult to install, such as yours.

---

### Post by Sabertootham on 2007-06-03
I tried that but it is also an iso image and it wouldn't boot from the cd.

---

### Post by confused57 on 2007-06-03
Here's how to burn an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Look for an option in your cd writing software for burning an iso as an "image", burn at a low speed(8x or less).

---

### Post by p_quarles on 2007-06-03
It sounds like you're doing everything right, so I'll offer these as just a couple shots in the dark:

1) I helped someone install Ubuntu on a Dell laptop the other day, and it required me to hold F12 on startup, and then set the boot order from there. 

2) Not all .ISO burners are created equal. For Windows, I've found ImgBurn to be a very reliable application. If you haven't already, try using that to create the CD.

---

