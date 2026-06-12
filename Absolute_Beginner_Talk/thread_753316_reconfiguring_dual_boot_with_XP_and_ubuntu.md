---
title: "reconfiguring dual boot with XP and ubuntu"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by aytackanaci on 2008-04-12
i had a dual boot configuration with win Xp and ubunu 7.10
then couple of days ago windows failed open
then i found this article about how to reinstalling windows on a dual boot system
[http://www.stoltenow.com/archives/2006/11/reinstalling_wi.html](http://www.stoltenow.com/archives/2006/11/reinstalling_wi.html)
but it's no use

now im stuck with windows and an ubuntu i cant boot

im guessing that the MBR has to be on the win partition on a conf like mine
if not can some1 tell me how to configure grub to boot my ubuntu and win from my ubuntu root partition
or can some1 tell me how to configure windows bottloader to boot ubuntu too.

i have 4 partititons
-sda1: windows and active boot partition
-sda2: /
-sda3: /home
-sda4
+-sda5: an ext3 partiton
+-linux-swap:

---

### Post by Oldsoldier2003 on 2008-04-12
> **aytackanaci said:**
> i had a dual boot configuration with win Xp and ubunu 7.10
then couple of days ago windows failed open
then i found this article about how to reinstalling windows on a dual boot system
[http://www.stoltenow.com/archives/2006/11/reinstalling_wi.html](http://www.stoltenow.com/archives/2006/11/reinstalling_wi.html)
but it's no use

now im stuck with windows and an ubuntu i cant boot

im guessing that the MBR has to be on the win partition on a conf like mine
if not can some1 tell me how to configure grub to boot my ubuntu and win from my ubuntu root partition
or can some1 tell me how to configure windows bottloader to boot ubuntu too.

i have 4 partititons
-sda1: windows and active boot partition
-sda2: /
-sda3: /home
-sda4
+-sda5: an ext3 partiton
+-linux-swap:

download the  [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/") and it will fix it for you. It will detect that you have a linux installation and install grub allowing you to dual boot Linux and Ubuntu.

You could manually install grub from the Ubuntu live CD but the SuperGrub CD makes it pretty painless :)

---

