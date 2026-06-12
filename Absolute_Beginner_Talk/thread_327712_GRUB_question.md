---
title: "GRUB question"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-12-29
Hi

I have Edgy Eft and Windows 98 installed as a dual-boot system on one partitioned hard drive with GRUB.

Please will someone remind me, when I did the Edgy install did it automatically install GRUB too or did it give me an option to say 'no'?:-k

---

### Post by jonathan.lees on 2006-12-29
Grub is installed by default. If you open a terminal > Application > Accessories > Terminal and type cd /boot/grub <enter> and ls it will list all the files in the grub folder that have been installed.

---

### Post by confused57 on 2006-12-29
> **ron999 said:**
> Hi

I have Edgy Eft and Windows 98 installed as a dual-boot system on one partitioned hard drive with GRUB.

Please will someone remind me, when I did the Edgy install did it automatically install GRUB too or did it give me an option to say 'no'?:-k

If you used the desktop live cd, I don't think it gives you an option...the alternate cd does.

---

### Post by benuski on 2006-12-29
The only option it gives you when you install is an option to change where you put GRUB.  The default is the master boot record, and thats where I've always put it, but you could put it somewhere else.

---

### Post by ron999 on 2006-12-29
OK, thanks you guys

If I connected another hard drive as a slave, and installed another distro on - even Feisty Fawn, do you think I could just add another line to Edgy's GRUB without installing yet another GRUB?

---

### Post by confused57 on 2006-12-29
> **ron999 said:**
> OK, thanks you guys

If I connected another hard drive as a slave, and installed another distro on - even Feisty Fawn, do you think I could just add another line to Edgy's GRUB without installing yet another GRUB?

Yes, you could install grub(Feisty?) to it's root partition, and add an entry in your Edgy grub to boot it by chainloading, e.g.:
title     Feisty
rootnoverify (hd1,0)
chainloader +1

I recommend using the alternate cd, if you want to specify where to put grub during installation...if perchance, your current mbr gets overwritten, you can always use the live cd to reinstall your Edgy grub to the mbr(hd0) and Feisty's grub to it's root partition(hd1,0):
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I've had to do the latter before, so I know it works very nicely.

---

### Post by Frak on 2006-12-29
in your grub configuration files, it will give you the exact prases to use when booting to another OS, like Windows is

title                Windows NT/2000/XP
location          hd(1,0)
makeactive
chainloader    +1
boot

Something like that, I'm in XP right now so I can't look.

---

### Post by louieb on 2006-12-29
> **ron999 said:**
> OK, thanks you guys

If I connected another hard drive as a slave, and installed another distro on - even Feisty Fawn, do you think I could just add another line to Edgy's GRUB without installing yet another GRUB?
The short answer is yes you could use the current distros GRUB and add an entry for the second distro. 
The longer answer is why you might want each distro to have its own copy of grub. Herman gives the pros and cons of each in his [Dual Boot]("http://users.bigpond.net.au/hermanzone/") site.

---

### Post by ron999 on 2006-12-29
Thanks folks.

louieb, I think you can see where I'm coming from... If I already have a perfectly good GRUB (Edgy's) why should I bother to install another GRUB when I add another OS.
If I can just add to Edgy's to give another option that would be neat.
I was intending to use the extra (small, second-hand) hard drive as a testbed for evaluating other OS's. Then when I'd finished, just un-modify Edgy's GRUB.

I'll read Herman's page to get more info.
:cool:

EDIT 
PS It seems the disadvantage is...
If I have W98, Edgy and Feisty using Edgy's GRUB...
If Edgy kernel gets updated - no problem, GRUB will be updated automatically.
But if Feisty kernel gets updated, GRUB won't be updated automatically.

---

### Post by Some_Person on 2006-12-29
It gave you an option at the very end about where to install GRUB. So, yes, GRUB is installed.

---

### Post by Frak on 2006-12-30
> **ron999 said:**
> But if Feisty kernel gets updated, GRUB won't be updated automatically.

All GRUB updates are the same, for all versions of Ubuntu, so no worry.

---

