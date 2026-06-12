---
title: "OSX + Win7 + 10.04, 15&quot; MBP"
date: 2010-08-24
forum: Apple Hardware Users
---

### Post by megabenman on 2010-08-24
Hey everyone,  I'm sure this question has been asked before but a searched didn't yield me any good results.  If this has already been asked please direct me to the thread :)

I have Ubuntu 10.04 on my previous main computer, an iMac G5 and I want it on my new main computer, the 2010 Macbook Pro.  I went into Bootcamp and made a 40 GB Windows partition leaving 460 GB for Snow Leopard + Ubuntu.  However bootcamp doesn't give me the option to make a new partition, only to erase my current 40GB partition.  Any help to make another 40GB partition for linux?  (420GB, 40GB, 40GB).  I'm thinking I'm supposed to just boot the live CD and cut the OS X partition from there?  Or maybe it would be easier to restore my OS X back to 500GB, then cut out a linux partition, then cut out a win partition using bootcamp?  I'm not sure haha, any help from people running this setup would be appreciated.

Don't know if it's worth mentioning but I do not intend to use rEFIt since I'll be using these partitions in mostly parallels, and although I doubt it voids my warranty I did get apple care and would rather not risk it for a nice boot screen.

---

### Post by Lars Noodén on 2010-08-24
[WINE on OS X]("http://www.tuaw.com/2010/01/06/how-to-run-windows-apps-for-free-with-wine-on-os-x/") is an option as is WINE on Ubuntu.  If there are any apps that don't run on WINE right out of the box, then post the name here.  You'll save a world of grief by leaving off Vista7 and any subsequent spawn.

To set up dual boot with Ubuntu and OS X or triple boot with a BSD:

1. Partition the HD using the OS X tools.  Make general partitions, the details for the secondary systems can be decided during the installation .

2. Install OS X
3. Install rEFIt
4. Install ubuntu and set up the ubuntu partitions in the space set aside in step 1 above.

One tip is that you can set up your Ubuntu home partition to use the HFS+ file system instead of EXT.  Then you can access it via OS X, too.  OS X appears to be drifting back away from Free and Open Source Software, at least interoperability is getting more difficult these days with 10.5 and 10.6.  One drawback with an HFS+ parition in Ubuntu is that during startup fsck won't deal with it properly and that makes some apps (eg KDE) lock up if the disk needs fscking.  Of course you can fsck manually, or boot to OS X and then reboot back to Ubuntu.

---

### Post by kennethsime on 2010-08-24
I would actually highly advise against using the OSX tools to create a windows partition. What bootcamp does is create a hybrid GPT-MBR partition table, which is uglier than ****. Although it shouldn't, what this did for me was create two different partition tables that did not agree. Instead, I would use GParted in the LiveCD to do your partitioning, and keep your GPT partition table in tact. If you've already created the hybrid mbr, I would try to use OSX to put everything back in it's place on a GPT table, and if that fails see [URL="http://ubuntuforums.org/showpost.php?p=9754054&postcount=8"this post[/URL].

---

