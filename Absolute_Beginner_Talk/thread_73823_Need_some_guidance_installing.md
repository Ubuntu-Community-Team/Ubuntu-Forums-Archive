---
title: "Need some guidance installing"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Souljah on 2005-10-10
Hi guys. Well this is my very first, actual linux distro on my computer. I have two computers, I'm not going to touch my main one, I'm going to install ubuntu on there. I'm going to format that whole computer so anyway, here's the deal. I want to dual boot with windows xp and ubuntuu. I have the preview release I think. Version 5.10. Anyway, which should I install first. XP or linux?

Now to the hard part. I've never ever done a linux installation so where do I start? :???: There's no installation file and I know you have to do some compiling so yeah. I have to burn it onto a cd and I have nero 6. Should I use that? If so, what options should I use?

I know I'm being a total noob here, but I am when it comes to linux. Some step by step instructions would be appreciated. Thanks and I'm looking forward to being a part of this community as I also plan on picking up some programming.

Ryan

---

### Post by Knome_fan on 2005-10-10
Hi,

first, install windows first, as it insists on installing its own bootloader which will make linux unbootable. Ubuntu on the other hand should pick up your windows install and configure a dual boot automatically.

second, make sure to leave some free space on your harddrive when you install windows, so that you can install linux on this free space later.

third, you won't need to compile anything.

forth, nero should be fine though I'm not really an expert here. Just make sure to not simply burn the iso file on CD, but to burn an image. (I think nero gives you the option under File -> Burn image)

fifth, to install, simply boot from your linux cdrom, that is, put it into your cdrom drive and start your computer. (Make sure that the computer is configured with your cdrom as the first boot device, of course)

sixth, have fun! :D

---

### Post by heimo on 2005-10-10
Hi! Congrats on decision to try Ubuntu! We'll be here to guide you through.

If you're doing completely fresh install, you should install XP first, then Ubuntu. No compiling during install is neccessary, everything is precompiled (binary). Sometimes it's neccessary to compile kernel, but for 99% it's not needed, updates are also available as "packages" - using very easy to use programs like Synaptic Package Manager and Update Manager (or my favourite, command line utility apt).

You need to get ISO file (cd image) from here:
[http://www.ubuntu.com/download/](http://www.ubuntu.com/download/)

Burn it using "from image" - open Nero Express and use "Disc Image" option on main menu. Use low burning speed, like 4x. Use BIOS settings to change boot device to cd drive, insert CD and ... the rest of the process looks pretty much like this:
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

:) Hopefully this clarified a bit.

---

### Post by Souljah on 2005-10-10
Wow. Well first of all, thanks for the very very fast replies. Indeed a large and helpful forum. Secondly, I will doing just that. In fact, after I post this message I'll probably be doing a complete format, installing Xp with service 2 and then install Ubuntu as you guys suggested. Just a heads up here, I forgot how to format my computer using XP. Lol, so funny. Just a little briefing here on how to do that? Just one more question, would 10 gigs be enough hard drive space for ubuntu?

---

### Post by brt on 2005-10-10
[QUOTE=Souljah] would 10 gigs be enough hard drive space for ubuntu?[/QUOTE]

usually this should be enough, my system with just some additional software takes now 3.5GB :)

---

### Post by heimo on 2005-10-10
No idea how to format hard disk in XP. :D Probably impossible if that disk is in use (impossible to finish cleanly), but there should be no need - I'm sure you can do that during XP install, just after partitioning.

10GB is enough for Ubuntu - you probably need somewhere around 3-4GB for "minimum" usable system - normally (for large disk) I'd recommend 6-7GB for / partition (that's the main partition, "root") and rest for /home (home directories), but if I used "only" 10GB for Ubuntu, I'd make it one single partition (others may have different opinion on this). You also need swap partition, 2x to 3x the size of RAM.

Maybe you could make two partitions - let's say, 7GB for /, 10GB for /home. Benefit of this arrangement is that you can do easy clean installs if neccessary. If you format XP disks as FAT32 you can use those too, but if you format using NTFS it will be read only for your Linux side of the system.

---

### Post by Souljah on 2005-10-10
[QUOTE=heimo]No idea how to format hard disk in XP. :D Probably impossible if that disk is in use (impossible to finish cleanly), but there should be no need - I'm sure you can do that during XP install, just after partitioning.

10GB is enough for Ubuntu - you probably need somewhere around 3-4GB for "minimum" usable system - normally (for large disk) I'd recommend 6-7GB for / partition (that's the main partition, "root") and rest for /home (home directories), but if I used "only" 10GB for Ubuntu, I'd make it one single partition (others may have different opinion on this). You also need swap partition, 2x to 3x the size of RAM.

Maybe you could make two partitions - let's say, 7GB for /, 10GB for /home. Benefit of this arrangement is that you can do easy clean installs if neccessary. If you format XP disks as FAT32 you can use those too, but if you format using NTFS it will be read only for your Linux side of the system.[/QUOTE]


I got some information on how formatting works. So I'm doing a complete fresh install. However, I did not understand the difference between root and home. What are they? I'm think root is something like C:/windows and home is just your stuff you put on? If I do make seperate partitions for home and root, would I have that options in the install?

---

### Post by heimo on 2005-10-10
It's been time since my last Ubuntu install, but I believe you choose manual partitioning during install and assign mount point (/ or /home) to each partition at that time. You pretty much understood what the / (also called root, but not to be mixed with /root which is homedirectory for superuser, root) and /home are.

Unix systems don't have drive letters (C:/D:), but a file system hierarchy where you can mount different devices. I could have single partition with everything on it, or partition for /, /tmp, /home, /var, /usr, /usr/local and so on. It makes the system very flexible, specifically when used with enterprise level systems like LVM and EVMS (something like dynamic disks in Windows world).

Normally you keep your personal files in home directory /home/username - and system files, like programs and libraries (a bit like .dll files) are in directories like /usr/share, /lib/modules and so on. No need to know about those at this time. Most systemwide configuration files are in /etc directory (user specific configuration files are in his/her homedir), Linux - the kernel itself is located in /boot directory. For temporary files there's /tmp and for "spools", printed jobs, emails and so on there's /var. On desktop system you probably need 3-4GB for all the neccessary programs and libraries, and couple gigabytes for other stuff - 7GB for / should be safe bet.

But I digress... :)

---

