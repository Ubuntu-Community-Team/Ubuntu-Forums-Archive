---
title: "switch from x86 to amd64 possible?"
date: 2008-01-12
forum: Apple Intel Users
---

### Post by phonky on 2008-01-12
I run an x86 installation on a MacBook Pro C2D  Intel(R) Core(TM)2 CPU         T7600  @ 2.33GHz

I tried the linux-rt kernel and have problems. I then found out that the sticky "apple intel users" post says for MBP post-2006 one can use the amd64 architecture.

Well, that probably won't solve my problem, but anyway 

- is there any reason to install the amd64 kernel, when I already run a x86?
- is there a possibility to install this via apt-get or the like or do
  I have to download the iso-file and install via CD?

Thanks for any contribution, greatly appreciated

---

### Post by Rog-Mahal on 2008-01-12
The 64 bit kernel does allow for some faster startup times for both your system and apps. It's a pretty mixed opinion on whether or not it's "better" I chose to go with 64 bit because I wanted to make full use of my Macbook's hardware. Some people have had problems with things like flash and running 32 bit apps, but there are compatibility libraries that have solved all my problems in that area. 

Someone else will have to speak to changing your package sources or not. Mine don't look like their architecture specific, but I'm not sure. That would be the main obstacle to switching via apt-get. To be safe, I'd just use the CD, unless you want to preserve all your settings and data.

Hope this is of some use. Cheers,

---

### Post by Tu13erhead on 2008-01-13
I'm thinking about doing this myself.

> **Rog-Mahal said:**
> To be safe, I'd just use the CD, unless you want to preserve all your settings and data.

How is the switch done without wiping all the data?  Is there any chance I can have both 32 and 64-bit versions installed and I can choose between them?

Thanks!

---

### Post by Rog-Mahal on 2008-01-13
Well, if it could be accomplished in the same manner as an apt-get upgrade, then all your data and gui settings remain the same, I am NOT sure that this is possible when changing the system architecture. 

here is an [old post]("http://ubuntuforums.org/archive/index.php/t-366707.html") regarding this topic, it looks like you'd have to do a complete reinstall. But, you might want to do some more research, perhaps things have changed.

---

### Post by cyberdork33 on 2008-01-13
yea i doubt that you can just "upgrade" as all the packages on your system are usually compiled for your arch.

---

### Post by phonky on 2008-01-23
Hmmm,

clearly upgrading via apt-get makes no sense.

What about dual booting via rEFIt - grub so that I can try the 64bit version for a while and then decide which one I'm going for?

That should be possible, shouldn't it?

---

### Post by cyberdork33 on 2008-01-23
> **phonky said:**
> Hmmm,

clearly upgrading via apt-get makes no sense.

What about dual booting via rEFIt - grub so that I can try the 64bit version for a while and then decide which one I'm going for?

That should be possible, shouldn't it?yes, although you have to be careful about the entries in Grub. The new install will overwrite grub (changing where it looks for config files) and create a new menu.lst (on the new partition). It is fixable, just be ready for it to happen.

If you had a separate home partition, you could use it in both systems as well.

---

### Post by Kevbert on 2008-01-23
Hi
I'm running both Ubuntu 7.10 64 and 32 bit on a single (but partitioned drive).  There seems very little difference between the two systems.  Why do I have both ?  I was lead to believe that it wasn't possible to run some applications in 64 bit, but so far no problems have occurred.  The only annoying thing is that the Grub bootloader shows both operating systems with the same name. :confused:

---

### Post by cyberdork33 on 2008-01-23
> **Kevbert said:**
> The only annoying thing is that the Grub bootloader shows both operating systems with the same name. :confused:You will probably have to go edit the menu.lst manually to get them to show differently... of course this will revert everytime you have a kernel update.

---

### Post by Kevbert on 2008-01-24
> **cyberdork33 said:**
> You will probably have to go edit the menu.lst manually to get them to show differently... of course this will revert everytime you have a kernel update.

Sorted thanks.  One thing was very strange.  Originally I had both systems with XP, on separate partitions on a single hard disk, and the menu.lst only detailed one installation of Ubuntu 7.10.  It did however boot all three OS.  Now I have two separate hard disks, one with XP Windoze and the other with new installs of both flavors of Ubuntu 7.10 (64/32 bit).  The new menu.lst file details both versions and this is the one I've edited.  The original menu.lst can be found here:
[http://ubuntuforums.org/showthread.php?t=247448&page=2]("http://ubuntuforums.org/showthread.php?t=247448&page=2") 
:confused:

---

