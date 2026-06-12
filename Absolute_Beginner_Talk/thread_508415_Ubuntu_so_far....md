---
title: "Ubuntu so far..."
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Thistlewait on 2007-07-24
This post is to relate my experiences with Ubuntu Linux so far. Up front I will state that my experience level with UNIX has been very limited. Professionally, I cut my teeth on DEC mini-computers (PDP and Vax). I was a VMS junky for many years. On the home-computer front, I started out with CP/M on Z-80 and 808x machines, and still adore the old Atari machines like the 800XL and my favorite dinosaur the Atari 1040ST running GEM. But, in all honesty my experience with UNIX is very limited.

I started "playing" with Ubuntu about five weeks ago. In recent years I've tried other Linux installations such as SUSE and RedHat but had a lot of difficulty getting them up and running, to the point that I considered them not worth the effort. Then, I caught an article on Google News stating that Dell was offering Ubuntu Linux on new machines. I thought that was a bold move and decided to check it out.

In a nutshell, I am very pleased with Ubuntu. The installation process was simpler and faster than any winstallation I've ever done. With the exception of a minor problem with my video display and an NTFS drive in the system, all of my hardware was correctly detected, drivers installed and working properly. The video problem was minor, and it took me less than an hour to get it straightened out.

That being said, I will confess that in the process of getting things straightend out, I did reinstall Ubuntu about a dozen times before I got an install that I think is stable and useable. Part of the reason for the multiple installs was to decide which desktop environment I preferred. I finally settled on KDE. But I also reinstalled several times because of the NTFS drive on my system. I have been unable to reliably mount that drive. I've had it mounted and able to access files on it twice. On the occasions when I could get it mounted and accessable, I don't really know how I did it. I try  to follow the same steps to get it mounted and accessable again, but sometimes it will...most of the time it  won't. Whenever I reboot the system the drive shows up in "Storage Media", but tells me that I don't have permission to access the drive. At this point, I have three different "Drive D" icons in "Storage Media", none of them will allow me access to the drive. I would like to just delete them, but I can't even do that. I admit that I'm frustrated with messing with that drive, and am just leaving it alone for now. So much for problems.

On the up-side, I am very pleased with the set of application suites that I've installed. The machine that I've installed Ubuntu on is the primary machine that I use for Internet access. I love Kontact, the KDE email and PIM application. Importing my old emails, folders, and address book from Outlook Express was fairly simple. I've also settled on Konqueror for a browser. I still have some issues with Konqueror that are mainly related to viewing video content. I'm a LiveVideo and YouTube junky these days. I don't have any problems accessing video on those sites, and I can also view videos in Google Video. But I still have problems accessing video feeds from IFilm, AtomFilms, and some of the online news sites that I visit. But, for the most part, Konqueror is working well.

I'm also a 3D Art and Animation hobbyist. All of my 3D, paint, and video apps run under Windows on a dual-core Intel machine with an ATI FireGL video card. I built and tuned that machine specifically for those purposes. But, since Blender has a Linux distributiion I've been playing around and having fun with Blender on my Ubuntu machine.

From time to time people I know will ask for my help building, repairing, or tuning their systems. Usually they have visited suspect web-sites or downloaded suspect software, picking up viruses in the process. I don't like to chase down viruses, and I usually recommend a clean reinstall on a newly formatted drive. Sometimes it is obvious that these people are running pirated versions of Windows. I won't install a pirated OS for anyone. I don't need the grief, and I try to convince them that they don't need the grief. It's not hard to understand why people will go down the piracy road. Most of them have built or acquired a computer "on the cheap", and they balk...or simply cannot afford to lay-out a couple of hundred bucks for a legal copy of Windows. More than once I've had irate confrontations with people because I won't do their bidding and install a pirated OS on their machines. Enter Ubuntu!

Recently such a situation presented itself. Someone needed help with their machine (running a pirated Win98 SE). I was able to show them Ubuntu Linux on my machine. And I was able to tell them that it is free and legal. The still have not agreed to make the switch because they are simply use to Windows and fear that what they have learned will not translate to Linux. So they took the machine back home, but...they are thinking about it.

The long and the short of all this is that I now have two machines running WinXP Pro, and one machine running Ubuntu Linux. I have come to consider Ubuntu more that just a toy or curiosity, it is a serious OS and I can accomplish serious work with it. If all of my 3D, paint and video apps were available under Linux, I would purchase Linux licenses for those apps. 

While this missive may not be an entirely glowing review of my experiences with Ubuntu, I hope that most will see it as a highly positive review.

Regards,
Thistlewait

---

### Post by buzzmandt on 2007-07-24
highly positive?  Yes......
You've tried many distros as I have and it is more than just a curious new toy, You have found (k)ubuntu to be a contender, As have I.

I use to use linux just for my online banking, now it's my primary OS.....And I run KDE as well.

I get my gaming fix from wine/cedega running oblivion, CoD, BF42, and Morrowind, I also run natively americas army 2.5 and quake 4 demo.

I also like pclinuxos, just sets up easier as far as streaming media and codex's go, but I feel i'm in control a bit more with *Ubuntu and I like the sudo gadget as opposed to su.

---

### Post by sad_iq on 2007-07-24
Well...I have converted some of my friends(actually all of them) to Ubuntu...but I have seen cases were they reverted because of some stupid things like the sounds you can send with yahoo messenger...or "i can't use the terminal thing...it's too hard for me"...I didn't know copy-paste was hard...but anyway...I can't force them(won't install windows either)...let them struggle :)  Now back to your problem(ntfs thing)...why don't you paste the output from this command ```
cat /etc/fstab
``` Let's see what we can do!!!

Edit: Don't mean to be rude or anything...but next time write only a few lines...most people here will avoid reading your problems because of the length of your message(and they do a lot o reading..man pages and all that..trust me)

---

### Post by meborc on 2007-07-24
you need "ntfs-config" package... you will then have a ntfs-configuration utility to set your mounting points... really easy

look for "ntfs-config" in synaptics or simply install it in terminal: "sudo apt-get install ntfs-config"

---

### Post by Tomosaur on 2007-07-24
It may interest you to know that you can run any number of desktop environments alongside each other without the need to reinstall the OS itself. In Synaptic package manager, the packages which will allow you to do this painlessly are:

> 
ubuntu-desktop
kubuntu-desktop
xubuntu-desktop


However, these packages also contain the default apps relating to that DE, so if you're worried about space, you may want to look into downloading just the individual packages to get the DE running. Once your DE of choice is installed, simply log out, click the 'sessions' button on your login screen, then choose which kind of desktop environment you wish to use :)

---

### Post by buzzmandt on 2007-07-24
> **Tomosaur said:**
> It may interest you to know that you can run any number of desktop environments alongside each other without the need to reinstall the OS itself. In Synaptic package manager, the packages which will allow you to do this painlessly are:
ubuntu-desktop
kubuntu-desktop
xubuntu-desktop


Good point, I always install ubuntu, configure nvidia driver, add codecs, then install kubuntu-desktop and run kde.  I'll switch from time to time, but usually run k.

In a terminal it's simply:
```
sudo apt-get install kubuntu-desktop
```

---

### Post by por100pre1 on 2007-07-24
> **buzzmandt said:**
> Good point, I always install ubuntu, configure nvidia driver, add codecs, then install kubuntu-desktop and run kde.  I'll switch from time to time, but usually run k.

In a terminal it's simply:
```
sudo apt-get install kubuntu-desktop
```

To install kubuntu-desktop with apt-get is NOT the best way. Use this instead:

```
sudo aptitude install kubuntu-desktop
```

I you want to uninstall it later:

```
sudo aptitude remove kubuntu-desktop
```

I'm using Ubuntu since May and very happy with it. :guitar:

---

### Post by ReverendJ1 on 2007-07-24
Another idea about the NTFS drive. Are you dual-booting? It may be that the last time you exited Windows it unmounted the drive correctly (or whatever it does when you shut down), i.e. you just shut the power off, instead of going Start -> Shutdown. If you do not have it already, install the 'ntfs-config' package, as meborc recommended, and then boot up Windows, and then shutdown Windows correctly. I have had problems with my NTFS drive while dual-booting and it seemed to always get fixed if I would boot into Windows and restart.

---

### Post by Majorix on 2007-07-24
> To install kubuntu-desktop with apt-get is NOT the best way. Use this instead:

It doesn't matter with whichever you install. You can remove dependencies installed with apt-get using:
```
sudo apt-get autoremove kubuntu-desktop
```

---

### Post by Mornedhel on 2007-07-24
Does that work with metapackages as well ?

It seems a bit dangerous to me... If I want to uninstall something I do not use (say, Ekiga), which removes the ubuntu-desktop metapackage, next time I want to do an apt-get autoremove, it wouldn't remove everything and its mother, would it ?...

---

### Post by armandh on 2007-07-24
it took a few hrs. to get comfy with the Ubuntu/gnome desktop but after that Im sold. no more not valid xp1
with 6 toys at the basement work bench 2 have 98se 2 have linux Ubuntu  and 2 have xp pro sp2 / ie7
those still on 98se are a bit underpowered for ubuntu/gnome

truely it is the fast/easy load of any os for a desktop IF there is enough mem and all the hardware works on the live CD test out.

---

### Post by Thistlewait on 2007-07-24
For sad_iq :

Hi,

Thanks for the offer to help. I appreciate it. 

FYI, I have installed ntfs-config but when I run it is just displays the "enable write" dialog. I check the "write" option, the app exits, and I still can't access the drive.

Let me know if another forum is more appropriate for this discussion.

Anyway, the following is my fstab file:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                    0  0  
# Entry for /dev/sde1 :
UUID=9887d88c-ab27-451d-b5ab-10f1cc647796  /               ext3         defaults,errors=remount-ro  0  1  
# Entry for /dev/sde5 :
UUID=ba721bad-a1e6-44ae-8d3c-609711d7e0b2  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sdf1                                  /media/DriveDD  ntfs-3g      users,_netdev,user,owner    0  0

---

### Post by Thistlewait on 2007-07-24
Regarding other desktops...

I wasn't aware that I could run different desktops side-by-side. Initially, Many of my reinstalls were because of disk space while testing. I was running Ubuntu as a dual-boot configuration with XP Pro on another partition. But, with my latest install, after backing up critical data  to a network drive, I ditched XP entirely am running pure Ubuntu as the only OS on an 80-gig drive. So, space isn't really an issue now, and I should have some latitude to play with some other destops...after I get the second hard-drive...the NTFS drive working reliably.

Thanks for the info.

---

### Post by stchman on 2007-07-24
> **por100pre1 said:**
> To install kubuntu-desktop with apt-get is NOT the best way. Use this instead:

```
sudo aptitude install kubuntu-desktop
```

I you want to uninstall it later:

```
sudo aptitude remove kubuntu-desktop
```

I'm using Ubuntu since May and very happy with it. :guitar:

Does not matter, since Edgy if you install with apt-get you can remove kubuntu by typing the following:

sudo apt-get autoremove kubuntu-desktop

Before Edgy you would be right.

---

