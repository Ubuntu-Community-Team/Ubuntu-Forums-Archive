---
title: "Questions about Feisty 7.04"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-19
- Will it require a complete re-installation losing all the software and files that I already have on 6.10?

- How do I make a Live CD? (I will be using my Windows XP to burn the disk) I would like to have a live CD rather than just doing a straight upgrade, in case something goes wrong and I need to put the live CD in again.

- Will read AND write be supported for my NTFS external hard disk?

---

### Post by freebird54 on 2007-04-19
Here we go:

1. It can be installed as an upgrade.  How well, I would give it a few days and monitor the forums to see!

2.  You make a cd by burning an IMAGE, not a file.  They exact terminology depends on what progam you use.  Some call it burning an image, some an .ISO burn etc etc.

3. NTFS read and write are supported on 6.10 as well.  It is better supported on 7.04.  The new kernel has better features (apparently) for ntfs-3g to use.

---

### Post by jem7v on 2007-04-19
> **Wake Rider said:**
> - Will it require a complete re-installation losing all the software and files that I already have on 6.10?

If you just do an upgrade your personal files Should be intact, but if you want to do a clean install it would be a good idea to have a separate /home partition.  Read here for how to do that:  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

As for losing programs?  Well, when upgrading from 6.06 to 6.10 I lost a lot of programs and had to reinstall them later, but the configuration files for those programs all survived.

---

### Post by old_geekster on 2007-04-19
The upgrade has been very successful.  I did two upgrades and both worked great.  This means no loss of previous data.

Here is the command that I used:

sudo update-manager -c -d

The Update Manager will open and inform you that Feisty 7.04 is available for upgrade.  Simply click to begin the upgrade.  At this point, there probably won't be too many updates after the install.

---

