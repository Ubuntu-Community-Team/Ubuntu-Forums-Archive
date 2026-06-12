---
title: "Triple Booting"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by JerryAtrik on 2007-06-26
Is triple booting a dodgy business or is it relatively straight forward .I already have Windows and Ubuntu Dapper on my system I now would like to add Feisty Fawn .Does Triple Booting have a high failure rate ? I will of course do all necessary backing up .
cheers Jerry

---

### Post by w4ett on 2007-06-26
As long as you  have sufficient space on your HDD, it'll work...Gparted will resize you partitions for you...just do good backups.

---

### Post by bodhi.zazen on 2007-06-26
> **JerryAtrik said:**
> Is triple booting a dodgy business or is it relatively straight forward .I already have Windows and Ubuntu Dapper on my system I now would like to add Feisty Fawn .Does Triple Booting have a high failure rate ? I will of course do all necessary backing up .
cheers Jerry

Triple booting should be straight forward as long as only 1 is windows. If you have more then 1 version of windows you may have problems.

Most OS will detect you previous installs & configure grub just fine. If you have problems with grub, check /boot/grub/menu.lst in your old install.

It can be tricky to boot the BSD's

Personally I install grub to the installation (root) partition and chain load.

title Ubuntu 
root (hd0,1)
chainloader +1
boot

title Fedora 7
root (hd0,2)
chainloader +1
boot

...

You get two grub menus that way, but each OS manages it's own kernel upgrades for you. I then configure grub on the root partition (second screen) to have a timout of 0 and bot the appropriate OS as default.

Boot 100+ OS
	[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

If yo do not chainload, you can make a boot partition or update /boot/grub/menu.lst manually.

---

### Post by overdrank on 2007-06-26
> **JerryAtrik said:**
> Is triple booting a dodgy business or is it relatively straight forward .I already have Windows and Ubuntu Dapper on my system I now would like to add Feisty Fawn .Does Triple Booting have a high failure rate ? I will of course do all necessary backing up .
cheers Jerry

Hi not a problem, I like to keep dapper around as a backup and since I have started with Feisty I have not need to use dapper but I am keeping it. Good luck!:popcorn:

---

### Post by reckless2k2 on 2007-06-26
My one machine has 5 different OSs running on it. I hear people talking about even more across different drives. I didn't find it difficult to do at all. If you can dual boot, you can triple boot.

---

### Post by JerryAtrik on 2007-06-26
Many thanks to you all for your reassurance .Will be going ahead later as soon as all the backing up is done.
cheers Jerry

---

