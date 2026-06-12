---
title: "where did my drives go?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by codlove on 2006-01-05
Hi guys

Just made the switch from winblows xp and trying to learn as much as i can about linux. I installed myself kubuntu breezy 5.10 and it seems great so far. I have a couple of questions if someone can explain them would be great.

1.
usually when I go in to System --> Storage Media I see my hard drive, my optical drive etc... I dont know what happened but now when I go there, there's nothing there anymore. Rebooting the computer doesn't help either. Did I mess something up?

2.
How do you install firefox 1.5? the website's install instructions make it seem so easy, but it doesn't work. I just found out how to install it using Adept, but still it bugs me to not be able to install from the source code because i've been searching and reading for hours and still am not able to do it.

Thanks in advance

---

### Post by bluefrog on 2006-01-05
u might have erased the whole disk while partitionning.
firefox 1.5, there is already a firefox on ubuntu, for 1.5 u should wait for ubuntu next release.

james

---

### Post by codlove on 2006-01-05
sorry james, i'm not sure what you mean, but my drives were there before.. and now I dont know why they've dissappeared.

---

### Post by Brokenrgv on 2006-01-05
just started using linux myself, you need to mount them to use them 
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by patrick295767 on 2006-01-05
u may use the bootable linux knoppix live cd to have a look to your harddisks and usb drives ... 
  
your weapons : 
nautilus, 
 
dmesg (to know where are installed your drives eg /dev/sda1
  
and: fdisk -l /dev/hda
  
Greetz

---

