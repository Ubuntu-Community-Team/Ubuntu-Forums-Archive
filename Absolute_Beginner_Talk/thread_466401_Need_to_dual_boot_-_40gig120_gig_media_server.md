---
title: "Need to dual boot - 40gig/120 gig media server"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2007-06-06
I installed Windows XP on a 40 gig drive and Ubuntu 7.04 on a 120 gig. I planned to use this as a media server. I would prefer Ubuntu only, but I unfortunately need some applications that don't work in Wine or other similar programs.

After I got everything configured how I wanted it, I realized that it might make more sense to have Ubuntu on the 40 gig and WinXP on the 120 gig, since Ubuntu can access the Windows drive, and vice versa not so easily (I don't think). My reasoning for swapping is that it is much more likely that I will need more than 40 gig for Windows than Ubuntu. Plus, Ubuntu can perfectly host a SMB share on a Windows drive, right?

Thoughts? Thanks!

Also, I should point out that right now, I can't get NTFS-Config to see my WinXP hard drive as an Internal drive. It seems to think it's external, and I can't write to it from Ubuntu. ("You do not have permissions to write to this folrder") Any ideas there?

---

### Post by gn2 on 2007-06-06
Use the NTFS and Fat32 auto-mounter that's available through [www.getautomatix.com](www.getautomatix.com)

It will automatically mount and make writeable all your NTFS partitions/drives.

Once you've installed Automatix, the auto-mounter is listed in the "Miscellaneous" category.

There isn't a simpler way and there's plenty other good stuff available through Automatix.

---

### Post by MartyNg on 2007-06-06
> **gn2 said:**
> Use the NTFS and Fat32 auto-mounter that's available through [www.getautomatix.com](www.getautomatix.com)

It will automatically mount and make writeable all your NTFS partitions/drives.

Once you've installed Automatix, the auto-mounter is listed in the "Miscellaneous" category.

There isn't a simpler way and there's plenty other good stuff available through Automatix.


Great! Worked like a champ! (Although I'm confused about the difference between Synaptic, Automatix, and Add/Remove Programs!) I'm sure a little research will help.

How do I go about removing the mounted hard drive icon from my desktop? Thanks so much!

---

### Post by gn2 on 2007-06-07
> **MartyNg said:**
> 
How do I go about removing the mounted hard drive icon from my desktop?

Not too sure, I use Xfce rather than Gnome.

With Xfce it seems that right-clicking on the Home desktop icon and choosing Desktop Settings gives the option to remove all icons but not individual ones...?

Gnome may well be different.

---

