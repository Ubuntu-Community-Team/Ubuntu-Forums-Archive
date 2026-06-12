---
title: "Dual booting on a Powermac G5 - formatting help"
date: 2007-10-31
forum: Apple PPC Users
---

### Post by Looper on 2007-10-31
Hi everyone. Complete Ubuntu learner here so bear with me please.

I have a Late 2005 PPC 2GHz G5 system for which I've just purchased a second internal SATA HDD (400GB). What I'd like to do is partition it, 20GB or so for Ubuntu 7.10 and the rest for my music/storage. Mac OS X will on the current HDD.

My question is really, what do I need to partition it as (as in, what file format) and then, once installed I'd want the computer to continue booting OS X (from the current HDD) as its primary OS - is that going to be a problem?

Thanks in advance for any help.

---

### Post by Auria on 2007-10-31
1) I'd consider keeping a CD of 7.04 around, 7.10 has a few painful problems for many PPC users and as a beginner you might not want to face them
2) Beackup important data, boot from the LiveCD, select the partitionner in the menus, shrink your OS X partition, leave the rest unallocated (i.e. do nothing with it, leave it empty)
3) In the installer, when it asks where to install, be careful not to select 'wipe entire disk' (well it's not written like that), instead choose 'install in free space'. then everything will be automatically created so you don't need to bother.
4) You will be able to boot directly to OS X. By default, it will boot to Ubuntu IIRC or maybe show a boot menu (ask which one). From there you have 2 choices that will both work:
- reconfigure yaboot (see in PPC FAQs and knowledge base, it's there somewhere) and make it do whatever you want at startup
- if you plan on using ubuntu only from time to time : hold down 'alt' during boot, select OS X, boot OS X, go in the System Preferences, go in the section where you can select which disk to boot, choose the OS X one.

hope it helps :)

---

### Post by frog_pilot on 2007-10-31
If you want to install ubuntu on your second hdd, there is nothing to do with your primary HDD with OSX.

Start the OSX Diskutility make your Partitions for Data-Storage. Make sure, that you leave about 20 Gigs as free space in front of the data-storage-partitions. do not take ubuntu gutsy gibbon as Auria said!

Use the alternate-PPC-CD to install ubuntu. When the installer starts, choose "take free disk space on Partition sdXX".

If you want to start OSX as your default-System. Open a terminal. Start a text editor in ubuntu with root-privileges and open /etc/yaboot.conf ```
sudo nano /etc/yaboot.conf
``` add the line ```
defaultos=macosx
``` after the line "macosx=/dev/hda<X>". After saving the changes to yaboot.conf, execute in the current terminal ```
sudo ybin
``` to write these changes to your bootstrap-partition.

If you leave the bootloader-process untouched it will now boot into OSX.

---

### Post by Looper on 2007-11-01
I tried installing 7.04, it just hangs mid-boot from the CD. 7.10 boots from CD fine and is (I think) installed.

Right, so I restart, hold down alt and then select the penguin. Yaboot loads. Now what do I do? What do I type to boot Ubuntu? It's installed in /dev/sdb2 (if that makes sense?)

btw, I'm typing this in Ubuntu 6.06 from my old x86 P3 laptop (wirelessly!) - it installed on that no problem! ;)

---

### Post by Looper on 2007-11-01
I'm a god damn idiot. You press 'return'. All working now! Thanks guys. I'm sure I'll have more problems to come!

---

