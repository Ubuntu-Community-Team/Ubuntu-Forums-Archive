---
title: "iMac G3 with OSX and OS9 already installed"
date: 2007-03-14
forum: Apple PPC Users
---

### Post by tanlaan on 2007-03-14
I wanted to know, can I install Ubuntu onto my iMac G3 that already has OSX and OS9 installed on without damaging my system? I've installed Ubuntu on it before *and had many a problem with gdm on it >.<, what gets me is that the problems changed*. I was just wonder, if I needed to resize the partition in OSX so it doesnt freak out, or will it notice that the partition table is changed when i install Ubuntu. Also, will I be able to get rid of Ubuntu without problems such as booting?

Thank you for the help in advance.

---

### Post by linear on 2007-03-14
Not sure what you're trying to do. Do you already have a separate partition that Ubuntu was installed on before, and you want to resize that? Or do you need to resize your OS X partition to make room for Ubuntu?

In general, setting up dual boot could go like this:

0. Read up in the PPC forums on any model specific quirks.
1. Back up your OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition the disk. Make two partitions. Leave the first as free space (unallocated) and the second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively (but a back up is prudent anyway).
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

This leaves you with a system that will default to booting Ubuntu. To change the default to OS X, see this: [http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

---

### Post by tanlaan on 2007-03-15
Thank you for the response. What I'm trying to do is install Ubuntu on my mac non destructively. I only have two partitions at the moment, one for OS 9 and one for OS X. Which means I need to use Parted to change the partition size. I should be able to install and remove Ubuntu without harming my OS 9 and OS X partitions/data at all right? If I chose to remove Ubuntu I could just use parted again to completely remove the Ubuntu partition and just tack it onto the OS X partition. Oh, one last question, do you know what I would need to do to remove grub? *a link to another forum topic would be great :D*

---

### Post by ssam on 2007-03-15
should work fine. but please back everything up before resizing partitions.

linux on mac hardware (from iMacG3s to the G5s)  uses yaboot instead of grub. it can be bypassed using the mac os (x) startup disk utility.

---

### Post by linear on 2007-03-15
> **tanlaan said:**
> I should be able to install and remove Ubuntu without harming my OS 9 and OS X partitions/data at all right?

Yes.

> If I chose to remove Ubuntu I could just use parted again to completely remove the Ubuntu partition and just tack it onto the OS X partition.Err... haven't tried it myself, but I recall reading that parted _will not_ be able to join the two partitions together.

---

