---
title: "Boot loaders info"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by M374llic4 on 2006-09-12
I saw in this post

[http://www.ubuntuforums.org/showthread.php?t=255846](http://www.ubuntuforums.org/showthread.php?t=255846)

That it shows windows xp. How do you set it up to load windows? 

I had xp on my system, tried to do a hd isntall of Dam Small Linux, I believe I was not supposed to write to the boot loader, I then installed GAG (Graphical Boot Loader). Tried to load linux and said boot record mising or invalid. 

Needless to say, windows is now gone, and linux doesnt work. I deleted all the partitions through a win2k disk I had laying around, do I have to create a partition to it? Not sure how to go about it totaly.

I have a friend downloading and burning me Ubuntu, so I can do it with that. I would rather not have windows installed at all, but my g/f requires it on the 2nd pc (which I am learning on trying to setup a server and such.) 

Do you have to reinstall windows, create another partition (extended?) then install linux and have it write to the boot loader? to get that style menu so I can select what OS i want? Do I not need the graphical boot loader? What if I want different Distros installed on the same hd?

Sorry for all the questions, hard to find actual people to answer them. : ) Thanks!

---

### Post by bulldog on 2006-09-12
If I understand you correctly you want to have a dual boot machine with XP an d Ubuntu??

Easy to do.
Install XP first but keep in mind to left some space for Ubuntu.[Minimum 10GB but more is better!] 

After installing XP, startup from the live Ubuntu cd and boot it.
On the desktop you see an install button which guide you through the install proces.

Just leave a peace of your hdd empty and unformatted for Ubuntu.
The installer does the rest for you.

At the end it will install GRUB which is a bootloader and it should have an entry for your Ubuntu as well for your XP so you can choose which one you boot.

---

### Post by dbd on 2006-09-12
I didn't quite understand, did you delete all your partitions? If you didn't then you should just be able to install ubuntu in the partition you had the other linux installed then it will fix the boot loader and windows will work again.

If you did delete the partitions then you need to repartition and install windows again. I'd advise you use the ubuntu live Cd to set up the partitions (since the ubuntu tool is easier to partition with than the windows tool) and then install windows and then go back to the ubuntu live cd to install ubuntu (windows will get rid of the boot loader if it is installed after ubuntu, so you want to install windows first).

[COLOR="black"]A little guide for partition sizes:[/COLOR]
Your windows C partition drive should be at least 5 GB. 
You need a swap partition, 256Mb will probably be ok, but search the forums and google if you want to be precise. 
I don't think your need 10Gb for the ubuntu root partition (mounted at /), 3.5 Gb would probably be enough, but the bigger the better. 
It's also probably making worth making another linux partition, to be mounted at /home this way if it all goes wrong and you have to reinstall then you can just format the / (root) partition and leave /home intact, so all your settings and stuff don't get lost in the process. Make this partition as big as you can, but remember, windows won't be able to read it.
After making those four paritions I'd make another partition taking the rest of your hard disk, with the fat32 filesystem so that both windows and linux can read it. 

Good luck :)

---

### Post by bodhi.zazen on 2006-09-12
> **M374llic4 said:**
> That it shows windows xp. How do you set it up to load windows?
When you install Ubuntu, as a part of the install you will install GRUB. During the instillation of GRUB the Windows partition will automatically be added to the boost menu and you should be able to boot windows XP no problem. 

> **M374llic4 said:**
> I had xp on my system, tried to do a hd isntall of Dam Small Linux, I believe I was not supposed to write to the boot loader, I then installed GAG (Graphical Boot Loader). Tried to load linux and said boot record mising or invalid. 

Needless to say, windows is now gone, and linux doesnt work. I deleted all the partitions through a win2k disk I had laying around, do I have to create a partition to it? Not sure how to go about it totaly.It may be possible to recover your windows partition if you have not formatted with your win2k disk, but it would take some effort and luck. Easier to start from scratch.

> **M374llic4 said:**
> Do you have to reinstall windows, create another partition (extended?) then install linux and have it write to the boot loader? to get that style menu so I can select what OS i want? Do I not need the graphical boot loader? What if I want different Distros installed on the same hd?

Sorry for all the questions, hard to find actual people to answer them. : ) Thanks!
In a nut shell, yes. Partition -> Install windows -> Install Ubuntu.

For a graphical guide try this:

[Graphical Ubuntu Install guide](http://www.psychocats.net/ubuntu/installing.html) [color=red]Thanks aysiu[/color]

---

