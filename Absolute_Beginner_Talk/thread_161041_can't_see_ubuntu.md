---
title: "can't see ubuntu"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by hassan on 2006-04-16
ok i installed ubuntu and got in serious trouble.
      here is the main thing.from start my pc is on xp home "japanese ".i amde 3 partitions for xp pro and ubuntu.now i installed ubuntu and it comes soomthly but after ubuntu i installed xp pro now my pc show only xp home and pro on booting pc.and have no access to ubuntu anymore.it shows in partition magic .any suggestions?
            should i format linux parition"ubuntu one" again?"linux ext3"or there is any shortcut for it?
                       desperately need your help guys.:(

---

### Post by htinn on 2006-04-16
You might just need to do a "grub-install /dev/somebootdevice" from the Ubuntu disc (in "rescue" mode, I think it's called).

---

### Post by hassan on 2006-04-16
but how to get linux screen is problem..when i restart my pc its directly shows to select xp home or pro to start ..sorry newbie here.

---

### Post by htinn on 2006-04-16
Okay, if your Ubuntu install CD doesn't have "rescue" mode, you could always try this:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

EDIT: Just found this in another thread:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by meistwer on 2006-04-16
Hi buddy,

As htinn said you need to go into rescue mode from the using the installation cd. Insert the cd before restarting, make sure ur BIOS config is set to boot from the cd-rom drive (u should do that before the PC starts booting up, if you dont know how let me know). Once that it's done then boot the computer and it should go to the installation process, from there look for recue mode. 

Besides you have learnt a great lesson today, how greedy is our friend Bill Gates. If you have any Operating System other than a Microsoft one when you install windows it will ignore it, he doesnt want you to use anything else but a microsoft one.

Good luck 

'Nobody Escapes The Algebra Of The Infinite Justice'

---

### Post by steve.horsley on 2006-04-16
Another point. Why did you use Windows to make a Linux partition? You don't use Linux to create a Windows partition before installing Windows, do you?

It is better to simply leave free space on the disk and tell the Ubuntu installer to use the free space. That way it can make the partitions it wants, with the sized it wants. If you create a partition for it and insist it uses that, it won't have a swap partition (unless you thought to create that which I doubt) and it will suffer poor performance.

---

