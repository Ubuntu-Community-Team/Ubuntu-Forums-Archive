---
title: "from Tiger to Ubuntu+Tiger"
date: 2007-10-09
forum: Apple PPC Users
---

### Post by marcozecca on 2007-10-09
hi!how can I install ubuntu after tiger?should I create partition?Should I use any software?can you explain me,please?

---

### Post by frog_pilot on 2007-10-09
If you now finally removed your ubuntu from your harddrive and did a fresh Tiger-Install it is much easier to create a dual-boot-system.

Before Installation of ubuntu you have to turn off the Journal within MACs filesystem to prevent data loss. Open a Terminal and execute```
sudo diskutil disableJournal /
```This turns off the Journal for the startvolume.

Now you can Install ubuntu and on partitioning you can choose "shrink existing partition". Or you can shrink it before ubuntu-Installation using gparted from a Live-CD.

After installing ubuntu, boot into OS X, open a Terminal and execute ```
sudo diskutil enableJournal /
```to restart the Journal on your OSX-Systemvolume. The whole rest of the installation will execute automatically and don't need your attention.

If you want to write on your OSX Systemvolume from within ubuntu, it 's recommendet to leave the Journal on MAC-filesystem turned off. But you can also create an extra vfat-partition to share data. Keep it in mind for the partitioning-process :)

---

### Post by marcozecca on 2007-10-19
ok I understood almost all!
I didn't understand this: "Now you can Install ubuntu and on partitioning you can choose "shrink existing partition". Or you can shrink it before ubuntu-Installation using gparted from a Live-CD."...what it means?what is gparted?is a software inside ubuntu live cd?and the live cd is the same cd I use for installing?

-another question: after installing ubuntu and restarting all, it will ask me to choose evreytime which o.s. to boot?or not?how does it work for it??

---

### Post by Auria on 2007-10-19
> **marcozecca said:**
> 
I didn't understand this: "Now you can Install ubuntu and on partitioning you can choose "shrink existing partition". Or you can shrink it before ubuntu-Installation using gparted from a Live-CD."...what it means?what is gparted?is a software inside ubuntu live cd?and the live cd is the same cd I use for installing?

yes, gparted is a piece of software included on the CD. There are 2 CDs you can use for installing : live and alternate. Live is nicer, alternate is usually more reliable.

While it usually goes just fine, remember partitionning is a risky operation so backup important data first

> **marcozecca said:**
> 
-another question: after installing ubuntu and restarting all, it will ask me to choose evreytime which o.s. to boot?or not?how does it work for it??

IIRC by default it will boot into ubuntu, but you can reconfigure it to ask wich one, or to pick OS X by default - it's all configurable from config files

---

### Post by marcozecca on 2007-10-19
so should I:
-insert cd of ubuntu 
-choose use live version
-partition my HD with gparted (is it already installed in ubuntu??where can I find it in Ubuntu?)
-restart all
-this time choose install, not live version
-install in the previously created partion

Am I right??:confused:

---

### Post by Auria on 2007-10-19
Actually there is 2 different CDs, the LiveCD and the alternate CD. Wich one you get is wich one you download. Both let you install Ubuntu, and there are no "modes". Alternate CD boots you directly in a text-based installer. LiveCD will start the system (albeit more slowly than usual) and you can try ubuntu before deciding to install. LiveCD has less chances of working than alternate but is nicer for beginners.

On the LiveCD (i cannot tell you about the alternate because for me LiveCD always worked) you will find the partitionner in the menus (it's quite obvious from the name). The best is to shrink your OS X partition and leave the remaining space empty (no partition). Then you can double-click on the "Install Ubuntu" icon and it will take you in the installer. When it asks you if you want to erase the whole hard disk, select 'use largest available free space' or something like that instead. Just be careful not to tell it to erase the whole disk if you want to keep OS X.

And of course as i said backup data first .
Good luck!

---

### Post by marcozecca on 2007-10-20
ok thanks!this week I think I'll do all, and I'll let you know!  :)

---

### Post by marcozecca on 2007-10-24
ok I did it and all has just gone ok!thanks to all of you!

---

