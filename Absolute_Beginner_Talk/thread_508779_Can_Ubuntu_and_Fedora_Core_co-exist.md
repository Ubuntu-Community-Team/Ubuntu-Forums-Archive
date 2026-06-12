---
title: "Can Ubuntu and Fedora Core co-exist?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-07-24
I think I know the answer but I have not been able to successfully install both and get grub to work right. I have received a number of tips on how to edit grub, etc. but so far nothing has worked. My last attempt was to install Ubuntu on a partition following W2K. Grub did fine with that. Then I set up another partition following the one where Ubuntu was installed and installed fedora core 6 there. Here is where the problems start. Although fedora said it installed successfully, when I rebooted, I went to a blank screen with the grub> prompt. Using some info I downloaded from the Super Grub Disk web site, I was able to get the Ubuntu grub menu.lst working again. But, I was never able to find the fedora core installation.

I am thinking of completely erasing and reformatting the hard drive and starting over. I wonder if I first create 2 or 3 partitions and do not install W2K but install Ubuntu 7.04 in the first partition and then install fedora core in the second partition, will they act nice and both be available in the grub menu. Or will I have to do a bunch of editing of grub's menu.lst?

I guess what I am asking here is 'Has anyone done this and what was their experience?'

---

### Post by Cypher on 2007-07-24
I think the installation of Ubuntu and Fedora should go smoothly until it's time to install GRUB. If you'd installed Fedora first and then install Ubuntu, when it comes time to lay down GRUB in the Ubuntu installer, you should see ALL the options that are available to you. If you don't see the Fedora partition listed, you should add it right there so that you don't have to worry about manually editing the GRUB menu.list file.

---

### Post by reckless2k2 on 2007-07-24
i already have this setup and it works fine.

---

### Post by Cypher on 2007-07-24
> **reckless2k2 said:**
> i already have this setup and it works fine.

I think it would be beneficial to all if you'd detail how you got GRUB and anything else that might interfere to behave properly. Stating that it works isn't very helpful. :)

---

### Post by rsnow on 2007-07-24
So, Cypher, do I understand that you recommend installing fedora first and then Ubuntu?

Also, would you be so kind as to give a brief description of how your disk is partitioned?

As a fairly newcomer to Linux I know it is early for me to be trying some of these things but my ultimate goal is to possibly have several different distros on one computer. I eventually would like to have one distro for general desktop use; one distro for a web server and one distro for graphics and video editing.

I have set myself a goal of learning as much as I can about Linux in a year's time. Then see if I feel comfortable enough with it to drop MS.

---

### Post by Cypher on 2007-07-25
I suppose if you're just going to install, say, 2 Linux Distro's on your computer. Then it doesn't matter in which order you install them as long as you ensure that during GRUB installation on the second OS, it lists the current OS and the other distro as well.

Ubuntu and Fedora both come with Live CD's that allow you to boot into a fully functional OS that allows you to explore all tha the distro has to offer before choosing to install it to the harddisk. That should be your first step as you will find there are unique differences between these 2 distro's and any other that you try.

I think having multiple distro's for distinct functionality is overkill especially since you can only be booted into one OS at any given time. So it's now like when you're using Ubuntu for general desktop use, the Fedora is also running providing Web Server functionality.

Additionally, the software that provides Web Server functionality (Apache) is the same across all distro's. So having it run in Ubuntu is no different than having it run in Fedora and so on..

So bottom line, play with the Live CD's of the various Distro's and when you've decided which one works best  for you, install it and enjoy..

---

### Post by rsnow on 2007-07-25
Thanks for your input. I value your opinion. Actually what you suggest is kind of my problem. I have both Ubuntu and fedora core live cds. I have looked at both but still have not been able to decide which one I like the best. I realize I can't boot into both at the same time, but I thought it might be helpful to have a setup where I could try doing certain things in each one and see if there was an advantage of one distro over the other. I'll eventually work it out. As to the web server, I may have misunderstood what I read- that one should use LAMPS and then seeing on the LAMPS web site that if was configured for RH and fedora. No other distros where mentioned.

If I can ask one more question, which distro would you choose if you wanted to edit videos with cinelerra on a AMD64 duo core , 2GB memory and Radeon X800 graphic card? Yours and any others opinions on this are welcome.

---

### Post by rsnow on 2007-07-26
Here is an update (in case anyone really cares:)) 

I cleaned the hard drive. I installed Ubuntu. I installed fedora. During the installation of fedora, I told fedora to add Ubuntu to grub and to make Ubuntu the default. Fedora did add Ubuntu to the list but it refused to make it default and the link to Ubuntu did not work. In other words fedora does not like to share... Kind of like MS.

So, now, I am going to try to install Ubuntu again and see what happens.

---

### Post by rsnow on 2007-07-26
O.K., let me close this thread with this last bit of info:

I have learned that if you want to have both Ubuntu and Fedora Core on the same hard drive, you should 1.) install fedora first and then Ubuntu or 2.) check the box that tells fedora not to install the boot loader if you already have Ubuntu installed.

Fedora's grub does not do a good job of recognizing other linux installations. Ubuntu's grub does nice.

Now, I have another problem I will post separately.

---

### Post by louieb on 2007-07-26
I've had up to a half dozen distributions on a single computer at the same time.
I've tried to configure GRUB in a few different ways By far the easiest an safest way is to chainload or use the configfile option with the configfile option being slightly easier.  
The short of it is one of the distros has its GRUB pointed to by the drives MBR. 
This is the GRUB menu that shows up first. 
When you install the 2nd, 3rd ... distro you:[LIST]
[*]install the grub pointer in the boot sector of that distros partition.
[*]modify the 1st distros GRUB menu.lst to include a configfile or chainloader entry.[/LIST]Easy to do and it works great. For a better explanation of both methods check out Herman's [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")   The most complete  dual boot site on the net. And Herman is a regular contributor this forum.

---

