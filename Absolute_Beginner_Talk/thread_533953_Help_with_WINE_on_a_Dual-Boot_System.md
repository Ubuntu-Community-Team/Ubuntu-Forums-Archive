---
title: "Help with WINE on a Dual-Boot System"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by jdimauro on 2007-08-24
Hi folks,

I recently installed Ubuntu in a dual-boot system on a computer with a Vista install (I have Ubuntu running solo on another machine).  I want to evaluate how some programs work on this better machine (World of Warcraft and some applications I need for work) to decide if I can make the switch to just using Ubuntu.  My question is, if I have the programs already installed in Vista, do I need to reinstall them with WINE as well or is there some way for it to recognize the Vista installations?

Thanks!
-John

---

### Post by WebSiteGuru on 2007-08-24
> **jdimauro said:**
> Hi folks,

I recently installed Ubuntu in a dual-boot system on a computer with a Vista install (I have Ubuntu running solo on another machine).  I want to evaluate how some programs work on this better machine (World of Warcraft and some applications I need for work) to decide if I can make the switch to just using Ubuntu.  My question is, if I have the programs already installed in Vista, do I need to reinstall them with WINE as well or is there some way for it to recognize the Vista installations?

Thanks!
-John

As to what I understand wine install the files in virtual c: drive (/home/username/.wine/c_drive/) So, I dont think that you can run any programs that was installed on Vista on Ubuntu. You will need to install it on Ubuntu.

But as far as for data, I think it would be ok to use it. If you have the data for both saved centralized in one place.

---

### Post by LowSky on 2007-08-24
you could run ubtuntu and  start vista up in a vitual server... but then thats just stupid.

Wine will let you install games, good luck getting them to work bug free

---

### Post by rexy on 2007-08-24
wine and vista really have nothing to do with each other, try installing using wine. The only reason where you would use something from vista is where the installation process fails. 

You can then try to copy over the game directory to the wine directory on ubuntu and then try to start the game using wine. Other then that you should never copy over any files from a windows installation to your wine directory as it breaks things horribly

Look on the[ wine]("http://www.google.com/search?q=wine+emulator") website for the list of games known to work with wine, they ussually include a small howto on how to get the game working using wine.

---

