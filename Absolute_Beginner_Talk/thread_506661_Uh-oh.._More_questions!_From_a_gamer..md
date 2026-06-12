---
title: "Uh-oh.. More questions! From a gamer."
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Booj2600 on 2007-07-22
Now, I understand Ubuntu is not the most gamer-friendly OS.  So, I had an idea how to improve that, and was looking for advice.

As it stands on the system I will install Ubuntu on, I have a 500gb hard drive, with Vista (windows) already installed.  My main question is what should I do from here..  Either dual-boot this machine and install ubuntu as well, or should I wipe it, create Ubuntu as the sole OS, and then use VMware Server (which I was informed was a free app for running other operating systems on top of Linux.. This is true, I hope?) to run Windows XP (the more gamer friendly OS, out of it and Vista) on top of it?  

Does this seem like a good idea?  Would I still be able to access Ubuntu files (music and the like) while I was running in Windows XP on VMware?  How hard is it to operate this virtual machine program?  Also, it then seems like I could simply uninstall the virtual XP, and make a virtual Vista when the time came..  Would all of the game files still be intact, then?  If that would all work..  Ubuntu would be the best system for me. 

Well, thank you for all your help!

---

### Post by benx009 on 2007-07-22
1) Ubuntu can be a pretty good gaming OS w/ [cedega]("http://www.transgaming.com/products/cedega/6.0/"), if you're willing to pay that is.

2) A dual-boot setup would be perfect for you (backup everything before attempting though!!!), so you can try out Ubuntu, and still game on windows, but I'm not sure how dual-booting works w/ Vista and I heard people had trouble doing just that because of some of Vista's new features.  But [here's a nice HOW-TO]("http://www.pro-networks.org/forum/about78184.html") if you're willing to take the risk.  Dual-booting Ubuntu and Windows XP is a piece of cake though.  I should know, as I'm doing it right now.

3) Yes, you can run Windows w/ VMware (and it shouldn't be too hard to set up), but you will undoubtedly have problems gaming, assuming that a game even starts up at all.  Just like another virtualization solution called "VirtualBox," DirectX is not supported by Vmware, though I've heard of a beta product called VMware Fusion that's trying to fix this.  Don't really know how that's currently working out though....

4) Here's my recommendation: dual-boot Ubuntu and XP (not Vista) and install Vista in Ubuntu through VMWare.  That way you can go crazy w/ Ubuntu, game on Windows XP, and still use Vista if you ever miss it (which you won't, or at least not until DX10 comes out. Then you might wanna go w/ a Vista reinstall if you have a DX10 video card...)

5) Unfortunately, Windows cannot access Linux partitions (I think those folks over at Microsoft like it that way) without special software, and I'm not sure how that'll work in VMware....

6) Good luck, and I hope you enjoy Ubuntu!!!:)

---

### Post by Booj2600 on 2007-07-22
Wow..  People aren't  kidding when they say these forums are helpful!  Thanks!  That was pretty much all of my questions in one fell swoop.  I didn't know that about VMware not supporting DirectX though.  Thank you for pointing that out and saving me tons of headache!  Much appreciated.  
Just one more question off the top of my head.  Can Linux systems freely access Windows files and play them?  I would prefer to save 30gb if I can and not have to put my music in both partitions.  Oh, I lied, by the way.  One more question.  When I dual-boot, to get to the other OS, does that mean I then have to completely restart my computer to switch?  Or is there (hopefully!) some faster way to do it, where I don't have to sit through the boot process everytime?  Well, in any case, thank you again!

---

### Post by RomeReactor on 2007-07-22
Hi.

> **Booj2600 said:**
> Can Linux systems freely access Windows files and play them?  I would prefer to save 30gb if I can and not have to put my music in both partitions.
I think you'll need to install a package called **ntfs-3g** in Ubuntu, which will allow you to read/write to ntfs partitions. I'm not sure if this is absolutely needed to just read files though, as I've never used it, but I think it is.

> When I dual-boot, to get to the other OS, does that mean I then have to completely restart my computer to switch?
Yes, you'll have to reboot to go into another of your installed systems.

---

### Post by jvc26 on 2007-07-22
Read only access to ntfs partitions is there in ubuntu by default, for read-write support you must use ntfs-3g (see instructions on the forums/the ubuntu documentation). I would definitely recommend using a dual boot for your gaming needs.
Il

---

### Post by ravenwere on 2007-07-23
Re music:

I have recently bought a usb external HDD and transferred my music and backups to that. If you go dual boot a fat32 drive can be accessed by both OS's saving the need to worry about which OS you boot into.

r

---

### Post by autocrosser on 2007-07-23
I've been playing UT2004 for several years in Linux--there is a native installer on the install disc & UT uses either Direct X or OpenGL so it's very easy.......

---

