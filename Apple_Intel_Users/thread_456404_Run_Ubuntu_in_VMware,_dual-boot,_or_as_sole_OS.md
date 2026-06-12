---
title: "Run Ubuntu in VMware, dual-boot, or as sole OS?"
date: 2007-05-27
forum: Apple Intel Users
---

### Post by thully on 2007-05-27
I was just curious-  what type of Ubuntu setup is everybody using on their Mac Intel machines, and why?
I've tested Ubuntu both in a dual-boot and in VMware on my MacBook, and they both have their ups and downs (dual-boot is faster and does 3D, but VMware allows fast access to OS X, easy data sharing, and better hardware support save for 3D and raw speed).  Currently, I'm leaning towards either giving Ubuntu alone a go or running in VMware - data sharing on a dual-boot is somewhat of a headache...

---

### Post by kingdomlyf on 2007-05-27
Hey, I am going to be triple booting, but am currently just dual booting.  I have a Mac Book Core 2 Duo.  the base model, but I upgraded the hardrive to 160 so I could use the lappy as my primary.  I have a 120-ish partition for the MAC-OSX and a 30-ish partition for Ubuntu 7.0.4 so far I haven't used the ubuntu much because I only have wifi, and am trying to figure out how to get the driver for my airport installed.  I know it's possible but am trying to find others who have done it with out getting the driver off of Windows.  As of right now I don't want to install windows if I don't have to.  But if I must to get the driver I will.  


proper stats - -- -  13" mac book core 2 duo 1.83 160 gig hd 512 ram.  
Using parallels for Ubuntu wifi and Solaris 10 and Fedora Core 4

---

### Post by mustang on 2007-05-27
Dual booting OSX and ubuntu but I never go into OSX---I just keep it there for firmware updates. It's also nice to have a backup operating system in case my primary one goes bad.

edit:
> **thully said:**
> I was just curious-  what type of Ubuntu setup is everybody using on their Mac Intel machines, and why?
I've tested Ubuntu both in a dual-boot and in VMware on my MacBook, and they both have their ups and downs (dual-boot is faster and does 3D, but VMware allows fast access to OS X, easy data sharing, and better hardware support save for 3D and raw speed).  Currently, I'm leaning towards either giving Ubuntu alone a go or running in VMware - data sharing on a dual-boot is somewhat of a headache...

BTW, would you care to elaborate "fast access to OSX, easy data sharing, better hardware support"? I'm not sure what you mean by fast access to OSX but easy data sharing---I had an easier time sharing files over a network in Ubuntu than I did in OSX. Same for better hardware support---it just hit me that I don't need to go hunting for drivers anymore. It was always a self-conscious exercise in windows---buy hardware, download drivers. But that's no longer the case. I remember when I only used OSX (ubuntu suspend wasn't working) and I wanted to print with my deskjet 970cse. OSX treated it as a generic printer which meant I couldn't change the print settings (ink, double sided printing). So I downloaded the driver from HP and that made the settings much more convoluted. There are literally 9 or so options in the drop-down menu for a simple printer---and I still couldn't find the print settings I was looking for!

---

### Post by thully on 2007-05-28
By "fast access to OS X" I was just alluding to the fact that you don't need to reboot when running under VMware.

By "easy data sharing" I was talking about the fact that you can share folders between the two OSes on one machine  in VMware easily, whereas doing this with a dual-boot results in glitches stemming from issues with HFS+ support.

Regardless, I'll likely do an Ubuntu single-boot, a dual-boot with a smaller OS X partition, or just stick with OS X (trying Fink/DarwinPorts/Gentoo for OS X for my GNU/FOSS fix)- I'm just unsure as to whether VMware Ubuntu would be worthwhile...

---

### Post by Seamyst on 2007-05-30
I have it as dual-boot, mainly using Feisty.  I do, however, highly recommend keeping at least a small partition for OS X, simply for when you encounter problems with Ubuntu or need to update firmware, etc.  Feisty works like a dream for me, for the most part - but I'm currently having trouble getting online at work in Ubuntu (works fine in OS X), and once a week or so I'll boot into OS X and run it for several hours, just to cool the computer down.

*shrugs*  For me, OS X is mainly my backup operating system, for when Feisty doesn't want to play for a while.

---

### Post by ronocdh on 2007-05-30
> **thully said:**
> By "easy data sharing" I was talking about the fact that you can share folders between the two OSes on one machine  in VMware easily, whereas doing this with a dual-boot results in glitches stemming from issues with HFS+ support.
False! There are plenty of posts here on this subject, so search at your leisure, but the long and short of it is that by disabling journaling on your OS X volume, Ubuntu will play nicely. As root you can grant your username r/w permissions on your OS X volume and add it to your fstab so it mounts at boot time. I've done this and I can use the same directory for files on both OS X and Ubuntu, effortlessly. =D

If you're interested in doing it, please search around and if you have any trouble at all, post about it and we'll get you all patched up in no time.

---

