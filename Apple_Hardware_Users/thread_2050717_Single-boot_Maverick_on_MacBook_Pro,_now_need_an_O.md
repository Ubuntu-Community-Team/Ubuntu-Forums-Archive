---
title: "Single-boot Maverick on MacBook Pro, now need an OSX partition"
date: 2012-08-31
forum: Apple Hardware Users
---

### Post by platz on 2012-08-31
A very unfortunate circumstance has arisen for me, the fact that I may NEED to use OSX for work, which has not occurred for me in many years. My normal work box is running Mint 12; but I've recently picked-up some involvement with a start up that is using Acquia Dev Cloud to host their application. Drupal is not new to me, but the Acquia cloud is. It turns out that in order to manage databases in a workflow that incorporates a local development server, one needs to use the Acquia Dev Desktop (xAMP) distribution, which (of course!) can't be used on a Linux desktop. I have an older Intel MacBook Pro that currently has a single-boot Ubuntu OS that I want to keep. Does anyone have any advice about adding a partition for OSX back to this clunker, before I dive in? I'd love to hear it!

---

### Post by Lars Noodén on 2012-08-31
I've run dual boot for years but have not found any good way to install both.  There might be another way, but the way that I've used has been to install OS X first and leave a partition or two for Linux.  Then install Linux after OS X is set and then install rEFIt to be able to boot between them.

---

### Post by platz on 2012-08-31
Yes, I've run dual-boot setups in the past with rEFIt, as well. In this case, I'd like keep my Ubuntu and just add the OSX.

---

### Post by Lars Noodén on 2012-08-31
Is your hard disk partitioned using GPT partition tables?  If not you will have to repartition.

I guess the key test will be what happens when you boot the install DVD or USB stick.  Can you go to the disk utility and resize the OS X partition without losing it?

The way I have gone from single boot to dual boot was to back everything up and then wipe the disk into three partitions: OS X, Linux and shared data.

---

### Post by platz on 2012-08-31
> The way I have gone from single boot to dual boot was to back everything  up and then wipe the disk into three partitions: OS X, Linux and shared  data.

That may be what I have to do.

---

### Post by Lars Noodén on 2012-08-31
(After backing up...)

You could try booting the Linux install CD and seeing if you can a) resize the partition and b) get the OS X install DVD to recognize/accept the empty partition.

---

### Post by Bachstelze on 2012-08-31
Another way (that may or may not be feasible for you) is to install OS X on an external drive. As a bonus you wouldn't have to modify your existing setup at all.

---

### Post by platz on 2012-08-31
If you have any insight into how to do that, please, do tell! I can imagine a world of headaches, but perhaps I'm as assuming too much.

---

### Post by Bachstelze on 2012-08-31
I have never done it myself but I think it just involves booting from the OS X DVD and installing normally, except you install on the external drive, not the internel one.

However if you are running Lion+ (meaning DVD-less) then I don't know...

---

