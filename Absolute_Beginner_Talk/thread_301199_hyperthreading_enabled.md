---
title: "hyperthreading enabled"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by b1g4L on 2006-11-16
By default will Ubuntu detect hyperthreading enabled CPU's and take use of the two logical cores? How can I check this?

---

### Post by rlozano on 2006-11-16
> **b1g4L said:**
> By default will Ubuntu detect hyperthreading enabled CPU's and take use of the two logical cores? How can I check this?

here's the information that can help you figure out your hyperthreading needs.

[http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)

hope this helps......

---

### Post by bollix47 on 2006-11-16
HT was detected automatically on my computer.  Go to System - Administration - System Monitor.

Look under resources and see if it shows 2 cpus.

---

### Post by Midway on 2006-11-16
I had mine turned off because of problems using it in Windows (such as the modem driver didn't like SMP) and I had forgotten I had it turned off in BIOS.  Last week I bought my first game for Linux, Quake 4, and I noticed it had a SMP version of the executable (I am assuming that is what this is).  So I enabled SMP in BIOS but I thought that since I had this "generic" kernel in Edgy I would have to upgrade the kernel for Ubuntu to take advantage of it.

Then I ran across this thread and checked my System Monitor:

[IMG]http://img296.imageshack.us/img296/9805/screenshotdk5.png[/IMG]

I am pleasantly surprised that this "generic" kernel saw my HT processor :)

---

### Post by b1g4L on 2006-11-16
Under resources, it doesn't show two CPU's so I do want to get this enabled. The link recommends I install the 686 kernel. Right now, I believe I have the 384 kernel. I'll search the forum for how to do this, but if some one knows, it would help a lot. Thanks!

---

### Post by MetalMusicAddict on 2006-11-16
> **b1g4L said:**
> Under resources, it doesn't show two CPU's so I do want to get this enabled. The link recommends I install the 686 kernel. Right now, I believe I have the 384 kernel. I'll search the forum for how to do this, but if some one knows, it would help a lot. Thanks!

If your using Edgy install the -generic kernel.

---

### Post by b1g4L on 2006-11-16
Is doing that through package manager ok?

---

### Post by autocrosser on 2006-11-16
Yes--that will work ok--And then take a look at the post above about HT..it was writen before Edgy came out....

---

### Post by b1g4L on 2006-11-21
I'm using the generic kernel now and I can see both CPU's. Nice! 

Can someone explain to me what's different between the generic kernel and the one that comes installed by default with Ubuntu (386). Also, while on the subject of kernels - is it possible to remove older kernels which I won't use any more. I want to clean up the menu.lst so only 2 or 3 kernels appear when grub loads. Thanks!!!

---

### Post by autocrosser on 2006-11-22
There are numerous How-Tos about editing your /boot/grub/menu.lst---I regularly update mine as things change--Open a terminal & do sudo gedit /boot/grub/menu.lst

this gives you--
1. root user permissions (use carefully!)
2. opens the document in Gedit

you can edit what you wish after that--but, please read some of the great how-tos before you just edit at will;)

---

### Post by b1g4L on 2006-11-23
I'm familiar with editing the menu.lst file, but does this "remove" the kernel altogether? In other words, I doubt I'll use older kernerls so there's no need for them to be on my computer still...

Also, can someone explain the difference between the 386 kernel and the generic one? I can't seem to find any documentation on the internet for the different kernels.

---

### Post by Bachstelze on 2006-11-23
1. To remve the kernel, the best way is to just remove the package through your favourite package management app. It will automagically remove the entry in sources.list as well.

2. In Edgy, you'll need the generic kernel to enable your HT, the 386 will be for 15-year-old-or-so CPUs. I don't know why the Ubuntu developpers dropped the various arch-specific kernels.

---

