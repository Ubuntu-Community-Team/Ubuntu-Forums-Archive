---
title: "Best way to try other distros?"
date: 2013-03-09
forum: Any Other OS
---

### Post by ShadowGuardian on 2013-03-09
I like Ubuntu alot, but i havent tried many others so my opinion does not have alot of weight.  I want to try other distros like Fedora, Arch, Mint, etc. 

However i don't know the best way to try them out.  Is it better just install them on a non-important computer, or live usb, or virtualbox?

I have installed fully on usb before, and that sounds like a good way to go, but I would like some opinions.

Thanks in advance!

P.S. This is about other distros, so i guess it goes here. :)

---

### Post by Paqman on 2013-03-09
Depends how you want to try them out. Virtualbox will let you have a look at the installer and a poke around the desktop, but if you want to get a feel for what a distro is actually like you can't beat installing it and using it as your everyday system for a while. Create another partition on your machine and start dual-booting.

---

### Post by tartalo on 2013-03-09
I usually try them first with a Live USB.

If the first impression is good then a Virtual Machine is the second stage. I try to customize them there, install the software I like, remove what I don't, try to understand how it works...

If I still like it after that, I have a partition were the best candidate to replace my current main installation goes, and I try to use it instead during a time.

---

### Post by ShadowGuardian on 2013-03-09
I already dual boot Windows (DONT YELL AT ME) and Ubuntu.  I dont like to mess with installing around windows.

---

### Post by Paqman on 2013-03-09
> **ShadowGuardian said:**
> I already dual boot Windows (DONT YELL AT ME) and Ubuntu.  I dont like to mess with installing around windows.

There's nothing wrong with dual-booting with Windows, anybody that tells you otherwise is an idiot.

You can still install more Linux distros even if you've already got two OSes. The easiest thing to do would be to not overwrite the original Grub entry and after installing the new OS go back into the origianl copy of Linux and run:
```
sudo update-grub
```
This will spot the new Linux distro and add it to the Grub menu.

However, if you're not comfortable with all this, then virtualbox is the way to go.

---

### Post by kiyop on 2013-03-10
> **tartalo said:**
> I usually try them first with a Live USB.

If the first impression is good then a Virtual Machine is the second stage. I try to customize them there, install the software I like, remove what I don't, try to understand how it works...

If I still like it after that, I have a partition were the best candidate to replace my current main installation goes, and I try to use it instead during a time.
+1 (I agree with the above idea.)

Usual Live USB does not change the contents in internal HDDs, unless you manually try to modify them.
Newbies tend to do wrong thing without knowing what they are doing is wrong.
If you can generate extra empty partitions correctly, you can install many linux distributions.
But some installers of some linux distributions tries to install some boot loaders onto MBR of a first internal HDD, which may cause some problem.
Thus, I suggest you copying current MBR onto some safe place before installing linux distributions.
Executing the following with root privilege will copy current MBR (and succeeding 62 sectors) of /dev/sda to a file "MBRbackup" in current directory:
```
dd if=/dev/sda bs=512 count=63 of=MBRbackup
```

---

### Post by MadmanRB on 2013-03-10
Virtualbox is good, but I also like liveUSB's as they offer a better hands on experience.

---

### Post by deadflowr on 2013-03-10
Virtualbox is great for the fact that you don't have to burn or create a usb stick.
It'll load straight from the folder as a virtual disk. Nice not having to deal with burning issues, and later realizing the distro sucks.

Personally, since I have an unquenchable sense of curiosity, I set up an empty partition on all my hard drives when I first install a main system. Usually at least 30GB. That way I always have an extra partition, I deem my testing/throw-away partition.

---

### Post by Markup 001 on 2013-03-10
I would narrow down the available options first off. Why not create a list of what you require from your distro and then make a list of each one available to you/your system. Differentiate between them by making a note of what each does well, or not so well. 
In this way you can move through your list, counting and discounting individual distros as you go. 
Hopefully before too long you should be left with a much narrower choice than you were faced with at the beginning of your search because there's a myriad of distros out there, offering (what appears to my inexperienced eye) limitless types of OSs to work with. 
I can't offer anything in the way of recommending individual distros because I am inexperienced re Linux for now, but I have jumped in to say that if you use a couple of lists to sort out exactly what you want and what each available distro can provide, then with less choices to go at, your task should hopefully be much easier. 

Good luck in your search, I have attempted puppy Linux as my first intro to Linux (its not going too smoothly :-)) so I will keep an eye on your topic to see what worked for you.

---

### Post by orb9220 on 2013-03-12
Yep for me usb or virtual may be better than liveCD experience. But found can't really give a real tryout until actually installing the distro.

The way I approach it is have just the 1 160gb hd. First 2 partitions is Win7 & Winxp and then have 3 partitions for linux. 1 for / 1 for /home and swap. 

Trying out distro's I use [Redo Backup]("http://redobackup.org/") to save partitions to external usb drive first thing.
Same as Clonezilla under the hood but a lot easier to use. 

During the install on partitions always use manual partitioning by selecting "Something Else" That way I can visually verify where partitions are assigned. And when assigning / "Root" partition. I like to install grub in same location as root partition. That way it doesn't touch windows MBR. And then just use Windows EasyBCD to add menu entry for linux on windows mbr.

That way mbr isn't touched and no need to constantly upgrade or fix grub constantly. It know as chain loading method.
Also when I back up root with [Redo Backup]("http://redobackup.org/") grub gets saved with distro backup.

/ and /home partitions are the only ones I need to backup each time I do a new distro. After originally backing up the whole drive that is with Win7,Winxp that is. I choose a separate /home for being able to clean install root without it messing with my personal data.

Backup or restoring just the linux partitions takes a whole 20mins and running prior distro that I have already setup and installed programs for a working desktop that fits my needs.

Have Bodhi,Funduntu,Ubuntu 12.10,Voyager 12.10 xfce,Linux Mint 14 Cinnamon and presently Linux Mint 14 KDE. All partitions backed up to external Usb drive. So can install back to a running setup with all the tweaks and adjustments for my use in 15-20 mins.

---

### Post by ShadowGuardian on 2013-03-12
I will probably use a usb to test out new operating systems and programs.  That being said I have one more question.  I am wanting to work with pentesting, so I looked at Backtrack and Blackbuntu.  Some mentioned that it would be best to just learn the ins-and-outs of linux, and find and learn the tools later.  I think this is a good idea, but I am going to go in a slightly different direction.

I want to make my own "Blackbuntu" using Ubuntu 12.04 (if you know of a better OS for this, please mention it).  

What is the best way to start?  What are some programs/tools to study and try? 

This will be a long-term adventure and I will learn along the way.

Thanks in advance.

---

### Post by mamamia88 on 2013-03-13
Best way to try a distro is to jump right in and install it on your main machine. That really is the best way to get a feel if its for you or not.  Just make sure not to accidently delete your main os partition

---

### Post by malspa on 2013-03-13
For me, I like to try a live session first, then if I like what I see, do an installation -- multi-boot set-up. Then keep using it for at least a few months, preferably longer. To get a feel for what the distro's all about, how it is over the long term. Most of the time (but not always), the longer I use a distro, the more I end up liking it.

---

