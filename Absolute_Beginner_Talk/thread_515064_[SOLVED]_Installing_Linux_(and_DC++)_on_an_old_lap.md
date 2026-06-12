---
title: "[SOLVED] Installing Linux (and DC++) on an old laptop"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by erk070 on 2007-08-01
I recently got an old IBM 390E laptop for free. I want to install some form of linux on it so I can run DC++ (I can't seem to get it to work in Windows 98 ). The laptop has an 300Mhz Intel Mobile Pentium II processor, 64MB RAM, and about a 4GB hard drive. :( I know this isn't great for Ubuntu, but I thought I'd try it anyway. I'm planning on installing Ubuntu with the alt CD. After doing some searching on these forums, I might try Xubuntu with the alt CD or DSL. And maybe fluxbuntu or some form of archlinux, but I'm not sure if my processor is the right architecture for those ones. I'm just looking for a small installation and hoping DC++'s install dependencies won't take up too much space. Does anyone have any other suggestions?

If none of those work, I also have a 250GB external hard drive that I might try to run linux from. However, it's formatted NTFS right now and has some data on it. I'd like to make it so I can keep that data, but also write data from linux that can be read by Windows (Windows on another machine - not planning to dual boot the old laptop). I'm guessing that would require NTFS, FAT32, and Ext2 on the same drive. Any help with this (even less Ubuntu related) topic would also be appreciated.

Thanks.

---

### Post by w4ett on 2007-08-01
You might want to consider Fluxbuntu:

[http://wiki.fluxbuntu.org/](http://wiki.fluxbuntu.org/)

Lightweight and designed for obsolete SLOW processors.  It is designed with your  type of equipment in mind...pretty impressive.

---

### Post by candtalan on 2007-08-01
It is also worth considering xubuntu, it is not so lightweight as fluxbuntu but is a lot easier for a newcomer to manage, for example, it has ready made menus!
The install method would need to be the alternate CD not a desktop (Live) cd because of the low RAM.
good luck

---

### Post by ugm6hr on 2007-08-01
On the laptop - a few points:

1. I would be surprised if you could get Fluxbuntu to install.  It is only available as a LiveCD, so getting it to run on a 64MB machine is going to be hard; installing from the LiveCD will be even harder.

2. Xubuntu is pretty good - but will probably be unbearably slow on 64MB too.  You could give it a try from the AlternateCD, and see if you can tolerate it.

3. If you really want an Ubuntu derivative - and can't tolerate Xubuntu's speed - try this instead: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Firefox might be a bit too slow on this, so again, give it a try - if it is unusable - there are plenty of other options (the link mentions dillo - which I think is too basic for regular use as a browser - other options are Opera or kazehakase or many others too).
This is another option if you don't like IceWM (although IceWM is a good choice if you are used to Windows): [http://ubuntuforums.org/showthread.php?t=396390](http://ubuntuforums.org/showthread.php?t=396390)

4. If you are looking for non-Ubuntu options:
a. DSL (as you mentioned) is very lightweight, and will run very fast on that system, but uses the 2.4 kernel, and is not the most user-friendly.
b. PuppyLinux is very good, and is my preferred option for sub-128MB systems where you are looking for out-of-the-box functionality.

I like Synaptic Package Manager in Ubuntu, and I think it's probably worth persevering with it if you want to do more than what Puppy does as standard (which is most things, actually).  The other issue is that Puppy logs you in as root (check psychocats for explanation on this).  Also - Puppy doesn't have Samba server as default (only Samba client), so file-sharing is not too straightforward.

Just some thoughts....

---

### Post by erk070 on 2007-08-10
Well, I've successfully installed Xubuntu from the alt CD and linuxdcpp. Fairly straightforward, but it does run slowly and the install took forever.. Thanks everyone.

---

