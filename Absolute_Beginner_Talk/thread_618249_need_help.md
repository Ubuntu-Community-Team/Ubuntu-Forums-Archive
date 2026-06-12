---
title: "need help"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by huziiik on 2007-11-20
Hi guys.I need help from someone.i have installed ubuntu and everything was fine,but than i reinstalled windows xp and my boot menu doesn t appear.how can i repair it??or how can i get to ubuntu?? :oops:

---

### Post by overdrank on 2007-11-20
> **huziiik said:**
> Hi guys.I need help from someone.i have installed ubuntu and everything was fine,but than i reinstalled windows xp and my boot menu doesn t appear.how can i repair it??or how can i get to ubuntu?? :oops:


HI and welcome, when you installed windows after ubuntu it writes over the mbr so you cant choose to boot. You will need to reinstall the grub and this link will help
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

---

### Post by Partyboi2 on 2007-11-20
This should help:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351:")

---

### Post by bumanie on 2007-11-20
This is a common problem. Windows thinks it is the only important thing. 
In terminal type 
sudo grub --> enter (this get you into the grub shell) -->
grub> find /boot/grub/stage1 --> enter
You will get output of the hdd partition grub is on. It will be (hd?,?). The first ? is the hard drive number (if you have only one hdd this number will be 0). The second number will be the partition number as recognised by grub.
grub> root (hd?,?) --> enter You insert the corresponding numbers in place of the ?
grub> setup (hd?) --> enter
grub> quit --> enter
This, all going well, should restore grub.

---

### Post by natehatewindows on 2007-11-20
also for the future you should make a super grub disk....it helps with these poblems a lot :)

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

