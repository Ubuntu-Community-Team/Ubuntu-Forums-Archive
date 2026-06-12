---
title: "installed Ubuntu, now want to install XP!"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by veritygold on 2006-03-23
Hello

This may seem crazy to many of you but I have installed Ubuntu and now want to install XP for dual boot purposes. Please allow me to explain the reasons for this for those who wish to know.

Yesterday XP wouldn't boot, so having had problems for a while I decided to reinstall, however this didn't work so instead I thought OK this gives me the incentive to do what I have wanted to do for a long while, install Ubuntu. No problems with that of course however I still need to use XP for somethings.

Question: Is it possible to now partition the hard drive and install XP? 

Note: When I installed Ubuntu I accepted all the defaults i.e. no partition. I am using version 5.10

Many thanks for your help. 

Nick

---

### Post by BlaineM on 2006-03-23
The way that I went about dual booting was to install XP first, which in your case was not an option, then add the Ubuntu install.  But I had to have the partitions written with space for the Ubuntu install left (free space)  I don't think that you can change a partition without affecting the information that is written to that partition.  So as to my knowledge, you would have to install Ubuntu not as the default, but with enough free partition space left to install your Windows partition.  I've also heard that Windows gets touchy if its not written on the first partition space, but you could dual boot multiple Windows OSs without trouble... I don't know if it can be the other way around, (with ubuntu first) I've never done it that way before.

---

### Post by veritygold on 2006-03-26
thanks

i managed to reinstall xp finally and now have partioned and installed ubuntu so all is cool

---

### Post by Sef on 2006-03-26
>  I don't know if it can be the other way around, (with ubuntu first) I've never done it that way before.

If you install Windows after Ubuntu, it wipes out GRUB, so you need to reinstall it. 


> I've also heard that Windows gets touchy if its not written on the first partition space, but you could dual boot multiple Windows OSs without trouble...

Windows needs to go on the first partition.  If you booted mulitiple Window OSes, then it would be on the first partition.

---

### Post by BlaineM on 2006-03-27
cool. thanks

---

### Post by cacahootie on 2006-03-27
The easiest way to reinstall grub, at least with the Dapper CDs, is to boot into Repair a Broken System, select the root drive, then reinstall grub.  However, last time I attempted to do this, it was still a tad buggy for my rather complex setup.

---

