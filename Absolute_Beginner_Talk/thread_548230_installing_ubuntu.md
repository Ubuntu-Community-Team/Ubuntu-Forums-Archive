---
title: "installing ubuntu"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by jemmyyong on 2007-09-11
I am about to switch from Windows to Ubuntu in my office for 10 computers..So I have to choose Ubuntu desktop edition or server edition? What is the different? is it possible e.g. 5 computers run Windows & others run Ubuntu both in the same network?

---

### Post by meborc on 2007-09-11
server edition will give you basic linux, WITHOUT a desktop environment... so no, you should use desktop version

---

### Post by lisati on 2007-09-11
> **jemmyyong said:**
> I am about to switch from Windows to Ubuntu in my office for 10 computers..So I have to choose Ubuntu desktop edition or server edition? What is the different? is it possible e.g. 5 computers run Windows & others run Ubuntu both in the same network?

The desktop edition would probably suit you better - it will be easier for other workers to make the transition. Any server requirements can then be setup later as required.

It is also possible to set things up so that some of your networked computers are Windows and some are Ubuntu, if this is what you need.

---

### Post by zipperback on 2007-09-11
> **jemmyyong said:**
> I am about to switch from Windows to Ubuntu in my office for 10 computers..So I have to choose Ubuntu desktop edition or server edition? What is the different? is it possible e.g. 5 computers run Windows & others run Ubuntu both in the same network?

Desktop edition is what you want.

Yes you can run 5 computers with windows and the others with Ubuntu.

- zipperback

---

### Post by jemmyyong on 2007-09-11
I decided to install Ubuntu to all computers..What about my Windows NTFS data ? I must copy them to new Ubuntu partitions or can I access directly? is there any applications to run my Ms Office & AutoCAD data?

---

### Post by BrendanM on 2007-09-11
Ubuntu has read access to NTFS enabled by default. If you want to write to those drives, you'll need to do "sudo apt-get install ntfs-3g".

OpenOffice can read/write (with medium-decent compatibility) MS Office documents. I don't know anything about AutoCAD.

---

### Post by lisati on 2007-09-11
> **jemmyyong said:**
> I decided to install Ubuntu to all computers..What about my Windows NTFS data ? I must copy them to new Ubuntu partitions or can I access directly? is there any applications to run my Ms Office & AutoCAD data?

[LIST=1]
[*]Even though Ubuntu can be "taught" how to read from NTFS file systems, it's probably a good idea to make a backup of your importanat data anyway, particularly while you're finding your way around
[*]Many of the programs that can be used with Windows have a Linux/Ubuntu equivalent. Ubuntu comes with "Open Office" which can use many of the same file types as MS Office
[/LIST]

---

### Post by jvc26 on 2007-09-11
I got this via a forum search, there may be other ones around.
[http://ubuntuforums.org/showthread.php?t=148488](http://ubuntuforums.org/showthread.php?t=148488)
And this is a link to the table of equivalent software.
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)
Il

---

### Post by armandh on 2007-09-11
since this is mission critical I would start 1 machine at a time. 
possibly dual boot for some time. 
during that time a fat 32  partition or NAS to transfer files. 
native read write by both os

---

### Post by jemmyyong on 2007-09-11
I've installed fresh copy of Ubuntu 6.06 LTS.. I try "sudo apt-get install ntfs-3g" but didn't work "E: Couldn't find package ntfs-3g".. What is going wrong?

---

