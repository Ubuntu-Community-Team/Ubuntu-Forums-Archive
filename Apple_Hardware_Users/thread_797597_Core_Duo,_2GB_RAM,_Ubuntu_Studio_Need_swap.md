---
title: "Core Duo, 2GB RAM, Ubuntu Studio: Need swap?"
date: 2008-05-17
forum: Apple Hardware Users
---

### Post by Aurora on 2008-05-17
Greetings,

I was making room for Ubuntu Studio 8.04 on my 2.0 GHz MacBook with Gparted; I didn't know whether to create a swap partition, or how large it should be, so I decided to abort and find out. Nothing relevant comes up when I search this thread or the Apple Intel FAQ thread.

Ubuntu Studio might be a lot more demanding in some cases than regular Ubuntu.  Recording audio with multiple tracks and plugins can use a lot of resources, but honestly I don't know if my projects will be that big.

Also, Ubuntu Studio uses an alternate CD with a different installer.  Would this be problematic?

I noticed I can boot off the live CD from the rEFIt menu; is this any different from booting while holding down C?  In other words, does it matter which one I do?

Thanks,

Paul in Seattle

---

### Post by Apple Ink on 2008-05-17
Firstly, I strongly recommend you to use BootCamp Assistant to partition your drive rather than gparted. This way you will save your self from the worries of Boot menu. You wont require rEFIt at all!

Secondly, it is suggested that you don have a separate partition for SWAP. Message me and ill tell you how to get on your root drive in Ubuntu!

And there is absolutely no difference between the Alternate CD and the normal one. Rather its sometimes best to use the alternate as it doesn't absorb too much resources on your machine!

And there is also n difference in rEFIt or C key in your Boot Menu!

Im running ubuntu on my 2.16ghz MacBook perfectly. Any problems, message me!

---

### Post by Apple Ink on 2008-05-17
And for your configs, you dont even need swap.

---

### Post by Aurora on 2008-05-17
I'd like to use gparted because the license expired on Boot Camp beta, so it won't install in Tiger.  I could set my machine's calendar back, but I'd rather not.  Or, I could pay Apple for an upgrade to Leopard, which includes Boot Camp Assistant, but I prefer not to.

So I just make a partition, format it, and install, just like that?  I'll try it and see: I have the Mac partition backed up just in case.

Ubuntu Studio uses a different installer that regular Ubuntu, I don't know why.

---

### Post by rlcomstock3 on 2008-05-17
Typically swap is 2x your ram amount.

---

### Post by Apple Ink on 2008-05-17
> **Aurora said:**
> So I just make a partition, format it, and install, just like that?

Yes, but the partition has to made by BootCamp ONLY. BootCamp while partitioning, edits the EFI to incorporate the partition sizes and boot options!

And Disk Utility or GParted will not do!

---

### Post by cyberdork33 on 2008-05-17
> **Apple Ink said:**
> Firstly, I strongly recommend you to use BootCamp Assistant to partition your drive rather than gparted. This way you will save your self from the worries of Boot menu. You wont require rEFIt at all!

> **Apple Ink said:**
> Yes, but the partition has to made by BootCamp ONLY. BootCamp while partitioning, edits the EFI to incorporate the partition sizes and boot options!

And Disk Utility or GParted will not do!

This is false. Boot Camp is not required to use the built-in boot menu system on your mac. All boot camp does is resize your OSX partition and create a FAT32 partition for Windows... that's it. All the other dual-booting items you associate with bootcamp is just your Mac EFI firmware.

> **Apple Ink said:**
> And for your configs, you dont even need swap.
I would definitely suggest a swap if you are planning to do intensive tasks with audio and/or video.

You can just use gparted to resize your OSX partition, and create a root and swap partition in the freed space. I would create a swap that is at least the size of your RAM as this will allow for hibernation.

After installing Ubuntu (studio) you can hold [alt] at startup to select your OS, or use rEFIt as a chooser. Keep in mind [there is a bug in the Ubuntu installer]("http://ubuntuforums.org/showthread.php?t=767677") that requires a rEFIt tool to fix, but I don't know if the bug affects Ubuntu Studio as well.

---

### Post by russo.mic on 2008-05-18
Just wanted to reinforce CD, bootcamp is not nessessary.  

Gparted can do everything you need, and doesn't cost anything. 
Bootcamp is kinda a joke, as OS X already contains the tools to partition, it just provides a thought free GUI. 

I had a swap when I had Ubuntu studio installed, and I found it never being used, so I killed it and had no problems.  Why don't you create one, and examine it's usage?  if it's not being used, kill it!  Your only giving up a few gigs anyway.  

CD, First i've heard of this issue.  interesting.  I didn't have it.  What gives?

Russo

---

### Post by cyberdork33 on 2008-05-18
> **russo.mic said:**
> CD, First i've heard of this issue.  interesting.  I didn't have it.  What gives?
Still not sure. I didn't have the issue either on a full reinstall...(although I did get the frozen refit screen) It is also not getting any attention from Ubuntu devs that I know of.

---

### Post by Aurora on 2008-05-18
Greetings,

I can boot OK in recovery mode, and am typing this on the MacBook in Ubuntu Studio.  Lots of fixing and tweaking yet to do, but the basic system is up and running.

I did not have the boot issues that others have have had; just a plethora of new ones--that will be another thread.

With Mac OS hogging most of the hard drive, a 2GB swap left me with an 8GB install--adequate if I use and external drive for audio sessions, as is standard for that kind of work.

Thanks to all for your kind assistance.  The community rocks :guitar:

--Paul in sunny Seattle :)

---

### Post by the8thstar on 2008-05-18
It may help or not, but you can easily use a swapfile instead of a swap partition.

Check the HOW-TO right here: [https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0]("https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0")

Enjoy!

---

### Post by Apple Ink on 2008-05-18
> **cyberdork33 said:**
> This is false. Boot Camp is not required to use the built-in boot menu system on your mac. All boot camp does is resize your OSX partition and create a FAT32 partition for Windows... that's it. 

Firstly, I dont see why would then the official macbook community page on ubuntu forums would suggest using BootCamp rather than Disk Utility!

Secondly, I myself tried using GParted 6 times to partition my internal drive with HFS+ and it failed hands down! Stuck at 15 or 17%...

Lastly, it is a well known fact that Partitioning a long running OS X drive is as tough as catching a black Mamba! BootCamp is to ease things out!

---

### Post by cyberdork33 on 2008-05-18
> **Apple Ink said:**
> Firstly, I dont see why would then the official macbook community page on ubuntu forums would suggest using BootCamp rather than Disk Utility!Disk Utility can only "add" partitions in Leopard. It is suggested in any install tutorials to use bootcamp or the commandline tools in OSX to resize. I am not saying you cannot use bootcamp, just saying using Bootcamp is not required to make a multi-boot system possible without rEFIt.

> **Apple Ink said:**
> Secondly, I myself tried using GParted 6 times to partition my internal drive with HFS+ and it failed hands down! Stuck at 15 or 17%...
Many people have used gparted to resize their HFS+ partitions without trouble. I am sorry that you had issues with yours, but it seems to be an outlier case.

> **Apple Ink said:**
> Lastly, it is a well known fact that Partitioning a long running OS X drive is as tough as catching a black Mamba! BootCamp is to ease things out!Certainly boot camp makes the partitioning process more user friendly, but it is quite limited in what it can do. I usually recommend using Bootcamp to resize and create a new partition, then before starting the installation in the Ubuntu LiveCD, use gparted to delete the bootcamp parition. Then you can choose to have the Ubuntu installer use the free space on the drive, and it does the rest of the work for you.

---

