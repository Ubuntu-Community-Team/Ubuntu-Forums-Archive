---
title: "Partition with Dual Boot question"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by tribeca26 on 2007-01-20
OK, so I'm attempting to install Ubuntu 6.10 on a computer that already has Windows XP on it. I want to dual boot both XP and Ubuntu. I have a single 80Gb hard drive which has 70Gb partitioned to Windows XP. I also partitioned 700MB as Swap and 5.6Gb partitioned for Ubuntu install (Ext3). And here's the part I need help with. When I get to the point in the Ubuntu install where I choose the mount points, I have no idea what to choose for my main partition with Windows XP so i do not corrupt it. Currently my choices read like so:

Mount Points:

/media/sda1                      68Gb            (Windows Partition)

Swap                                698MB           

/                                       5Gb

These are the defaults that come up. Firstly, what do I choose for my windows partition (currently: /media/sda1) so I can dual boot and it does not corrupt it?? And what do I choose for my two other partitions?  And secondly, can someone explain what exactly a mount point is? I've searched for hours on how to dual boot like this, but cannot find the answer. Any help would be highly appreciated :grin: I am new to linux and do not really understand all the lingo so please dumb it down for me :wink:

---

### Post by housam on 2007-01-20
DO not choose any thing for windows , you already have it on your HDD. You will choose only to reformat the partitions for the root ( / ) and for the swap. Just click on-front of this two partitions only. make sure of that.
At the end of the installation Ubuntu will install a grub booting loader which will allow for the dual boot. Don't worry about that.

---

### Post by mikewhatever on 2007-01-20
The defaults you posted are fine. Read here about mount point [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

You can also read this guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) for more examples.

---

### Post by tribeca26 on 2007-01-20
> **housam said:**
> DO not choose any thing for windows , you already have it on your HDD. You will choose only to reformat the partitions for the root ( / ) and for the swap. Just click on-front of this two partitions only. make sure of that.
At the end of the installation Ubuntu will install a grub booting loader which will allow for the dual boot. Don't worry about that.

So for the Windows Partition I use the pull down menu and select the blank option? or leave it the way it comes up as default? And could you please clarify what you mean by "Just click on-front of the two partitions only" thanks :)

---

### Post by mikewhatever on 2007-01-20
> **housam said:**
> DO not choose any thing for windows , you already have it on your HDD.

In this case Windows partition will be inaccessible from Ubuntu. It, however, can be mounted manually.

---

### Post by tribeca26 on 2007-01-20
> **mikewhatever said:**
> The defaults you posted are fine. Read here about mount point [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

You can also read this guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) for more examples.

Thank You mike! i am starting to understand this. So if i choose /media/sda1 for my windows partition, I will be able to dual boot with it and it will not corrupt my XP install?

---

### Post by mikewhatever on 2007-01-20
> **tribeca26 said:**
> Thank You mike! i am starting to understand this. So if i choose /media/sda1 for my windows partition, I will be able to dual boot with it and it will not corrupt my XP install?

Mounting is done to have access to your partition after the installation. It has nothing to do with corrupting partitions. If, for example, you mount in /media/hda1, then you'll have a folder called 'media', and inside it a folder called 'hda1' which is like a door into your Windows partition. See the screenshot of my media folder.

---

### Post by housam on 2007-01-20
Preparing for the mounting points is pointing to the partitions that ubuntu will be installed on it. i.e. (/)for the root and swap for swap . ubuntu need to reformat these two partitions to prepare them for installation. that is why you should click in front of them under the column of reformat.

For windows-xp partition, leave it as the default come up.

You can read [this link]("http://www.psychocats.net/ubuntu/installing").it is a great guide for installation.

---

### Post by tribeca26 on 2007-01-20
Alright I appreciate your help tons! I will go have some fun with Ubuntu now :biggrin:

---

