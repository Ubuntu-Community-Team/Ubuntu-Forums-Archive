---
title: ":: suse installed now want to have UBUNTU::"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by mohsin on 2005-08-07
hello guyz .. 

 well i have installed suse 9.1 before it .. 

 i without changing any thing start installing ubuntu it goes all well but when partitioning comes 

 it give problem i removed all the data from the drive suse installed .. swap is as it is .. 

 setup is giving error of /root is not defined .. or allocated now what i should do 

 simply to create root .. while suse created already :( 


 thnx . for helping hope that you people got me 

 :)

---

### Post by roland on 2005-08-07
[QUOTE=mohsin]hello guyz .. 
 well i have installed suse 9.1 before it .. 
 i without changing any thing start installing ubuntu it goes all well but when partitioning comes 
 it give problem i removed all the data from the drive suse installed .. swap is as it is .. 
setup is giving error of /root is not defined .. or allocated now what i should do 
 simply to create root .. while suse created already :( 
 thnx . for helping hope that you people got me 

 :)[/QUOTE]

What partitions do you have? Maybe the /root directory should be mounted on another partition than the / directory. Is SuSE still working? If it is, could you copy/paste your /etc/fstab file here (assuming everything works fine with SuSE)? That is done by opening a text editor like KWrite (it should exist in SuSE), and opening /etc/fstab. Maybe I can then help you.

---

### Post by mohsin on 2005-08-07
no suse cant run now .. grub bash error .. 

 so what now next ?

---

### Post by N'Jal on 2005-08-07
fdisc /dev/hd**

delete all partition's start again from scratch

You can get fdisc from the gentoo installer

---

### Post by roland on 2005-08-08
[QUOTE=N'Jal]fdisc /dev/hd**

delete all partition's start again from scratch

You can get fdisc from the gentoo installer[/QUOTE]

Formatting all partitions is a bit of a rigourous solution to the problem. However, SuSE and Ubuntu have a significant difference in file locations, especially shared libraries and stuff. If you have one root partition (the / directory) and one or more partitions for data storage only, you could think of installing Ubuntu and leaving the data intact. If you have different partitions for [font=courier]/[/font], [font=courier]/var[/font], [font=courier]/usr[/font] (maybe even [font=courier]/boot[/font]) and so on, it would be wise to install Ubuntu from scratch, really formatting each partition.

Also fdisk is written with a **k** instead of a **c**.

---

