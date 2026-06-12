---
title: "The Ability to Have Windows and Ubuntu"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Zander747 on 2007-08-11
I thought the answer would be a bit more obvious, and I could easily find out, but I can't so I'm asking the community.

When you install Ubuntu, does your windows partition stay on another partition, or does Ubuntu wipe windows all together? If it does wipe windows, how do I make it so I can choose to boot Windows or Ubuntu? I'd like to keep both operating systems if possible.

---

### Post by MenZa on 2007-08-11
Well, you normally install Windows and leave some unpartitioned space for Ubuntu to use. Ubuntu will during the installation detect any operating systems you may have installed already and give you a bootup manager on startup.

---

### Post by Zander747 on 2007-08-11
> **MenZa said:**
> Well, you normally install Windows and leave some unpartitioned space for Ubuntu to use. Ubuntu will during the installation detect any operating systems you may have installed already and give you a bootup manager on startup.

Ok, so if I install it, windows will still be their? Also how can I set a limit to the ammount of space I can use up on Ubuntu?

---

### Post by zvacet on 2007-08-11
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by steve.horsley on 2007-08-11
Hace a look at thei:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
especially the 8th picture, and the section titled Dealing with Partitioning

EDIT:
SNAP!

---

### Post by jeremy1138 on 2007-08-11
> **Zander747 said:**
> I thought the answer would be a bit more obvious, and I could easily find out, but I can't so I'm asking the community.

When you install Ubuntu, does your windows partition stay on another partition, or does Ubuntu wipe windows all together? If it does wipe windows, how do I make it so I can choose to boot Windows or Ubuntu? I'd like to keep both operating systems if possible.

I used Norton Partition Magic to repartition my hard drive so that I could keep my existing Windows installation and make room for Ubuntu.  It worked great and I've been running this dual boot system since version 7.04 came out earlier this year.  One piece of advice that I can give you is to just use the boot loader that comes with linux and do not under any circumstances use Norton Boot Magic!  I do believe that during the installation of Ubuntu you are given the option to wipe the hard drive and have Ubuntu set things up the way it wants or you are given the option to set up things to your own liking.  So you should be able to have a dual boot system and keep windows if you wish.

---

### Post by Paul133 on 2007-08-11
If you install it the right way, Window swill still be there. When you install Ubuntu, at one point, you'll be given the option to partition the drive or wipe Windows or use the largest amoutn of free space. You might not have any free space. In that case, you have to manually partition the drive. You'll see your windows partition and you'll have to shrink it. Then yu can go back and use the free space to install Ubuntu, or you can manually parittion the drive. If you choose to manually partition the drive, you'll need to make a "/" partition using the Ext3 filesystem and a swap partition. You also probably want an Ext3 "/home" partition. More info on partitioning is available here: 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

edit: Wow; we all love aysiu's site!

---

### Post by steve.horsley on 2007-08-12
> **jeremy1138 said:**
> I used Norton Partition Magic to repartition my hard drive so that I could keep my existing Windows installation and make room for Ubuntu.
This is a good approach if you have partition magic. However, make sure you just leave free (unpartitioned) space for the Ubuntu installer - don't try and get clever and create a partition for it. Then tell the installer to use the free disk space and it will make its own partitions - it will probably create 3 partitions of 3 different types - an Extended partition, an ext3 partition for the data and a swap partition for virtual memory.

---

