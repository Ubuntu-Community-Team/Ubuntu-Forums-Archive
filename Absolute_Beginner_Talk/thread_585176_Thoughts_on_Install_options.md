---
title: "Thoughts on Install options"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by JohnCorbin on 2007-10-21
I am planning on installing Ubuntu.  There are, I am told a few options on were to install it.

I am now using UNIX at work and need a way to practice scripting and some basic AWK, SED stuff as well...

I am currently running Winblows XP Home edition on 3.7 ghz machine.  3 gigs of ram and 2x256 meg video cards on PCI express machine.

I can install it on..

**_1 - A partition on my main hard drive._**

I am leary of this is as I am not sure how to partition a hard drive with out have to reformat and go all through re-installs of existing windows software.  My main hard drive is 160 gig and I have about 111 gig free.

_**2 - I have an external USB 160 gig drive.**_

Any thoughts on installing this way would be appreciated.  I can make it
totally avaialble...

_**3 - I have recently stumbled accross VMWare.**_

From what I have read..  this sounds interesting...  But some input would be nice.

Personally..  Option 2 is where I am leaning.

---

### Post by forestpixie on 2007-10-21
have a look at this [page]("https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed") - there is info on installing to an external

---

### Post by aysiu on 2007-10-21
If you have 3 GB of RAM, install Ubuntu using VirtualBox in Windows:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by bodhi.zazen on 2007-10-21
> **JohnCorbin said:**
> I am planning on installing Ubuntu.  There are, I am told a few options on were to install it.

I am now using UNIX at work and need a way to practice scripting and some basic AWK, SED stuff as well...

I am currently running Winblows XP Home edition on 3.7 ghz machine.  3 gigs of ram and 2x256 meg video cards on PCI express machine.

I can install it on..

**_1 - A partition on my main hard drive._**

I am leary of this is as I am not sure how to partition a hard drive with out have to reformat and go all through re-installs of existing windows software.  My main hard drive is 160 gig and I have about 111 gig free.

_**2 - I have an external USB 160 gig drive.**_

Any thoughts on installing this way would be appreciated.  I can make it
totally avaialble...

_**3 - I have recently stumbled accross VMWare.**_

From what I have read..  this sounds interesting...  But some input would be nice.

Personally..  Option 2 is where I am leaning.

If you have sufficient RAM, virtualization can be nice, especially as you do not need to keep re-booting.

I would look into DSL or puppy linux, they are light weight and you can get familiar with the command line easily.

See this sticky for information on virtualization :

[http://ubuntuforums.org/showthread.php?p=3577560](http://ubuntuforums.org/showthread.php?p=3577560)

If you like, you can easily dual boot :

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by benerivo on 2007-10-21
> 1 - A partition on my main hard drive.
This would be my preferred option, using the partition manager from the ubuntu live cd. You would need to defragment the drive from xp, at least once. Then load ubuntu and shrink the xp partition to make a new partition to install ubuntu on. The installation will automatically set up a dual boot, so that you can choose xp or ubuntu when switching on.

> 2 - I have an external USB 160 gig drive.
Would also work, but it involves a couple of considerations related to where the boot loader will be installed. A normal second drive installation will place the boot loader on to it, so the drive will have to be connected if you want to run xp. There is a way around this, if you choose to put it on your usb.

> 3 - I have recently stumbled accross VMWare.
Can be useful for specific purposes such as running several os's without rebooting or having 10+ partitions, but dual booting is a bit simpler.

---

### Post by HermanAB on 2007-10-21
If you base system is working properly and you wish to experiment, then I suggest that you install the free vmware server, since you can then go nuts in a virtual machine, without breaking your host system.  

Just go to the VMware web site, look for free VMware Server, give them your whole pedigree and you will get 10 keys.  Save the keys and follow the instructions to install VMware.  I have installed it numerous times without much trouble.

You can run anything on VMware.  There are faster systems like Qemu and Virtualbox, but they cannot run everything - Win2003 will crash for example.  Other systems like Xen and others can only run Linux in VMs.  So slow and sure is sometimes best.

Cheers,

Herman

---

### Post by JohnCorbin on 2007-10-21
> **aysiu said:**
> If you have 3 GB of RAM, install Ubuntu using VirtualBox in Windows:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

OK..  I read the info but I may have misread something ..  or I was not clear in my original question...

I go to this link:

[http://ubuntuforums.org/showthread.php?p=3577560](http://ubuntuforums.org/showthread.php?p=3577560)

and find the Virtual Box how to...

[http://ubuntuforums.org/showthread.php?t=340113](http://ubuntuforums.org/showthread.php?t=340113)

If I tread this right..  It is assuming that I am already running Bantu..  I am not..

There is a bit in there that says Open With -> GDebi.

Any thoughts...

---

### Post by bodhi.zazen on 2007-10-21
If you are running windows, you need to install the windows version of Virtualbox

---

### Post by JohnCorbin on 2007-10-21
> **bodhi.zazen said:**
> If you are running windows, you need to install the windows version of Virtualbox

Great..  got Virtual box installed
set up a Virtual Drive


How do I install Ubuntu ?

---

