---
title: "uninstall/reinstall onto external hard drive"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by superjeff on 2007-08-10
i'm dual booting ubuntu and vista home premium on a single 120 gig hdd, and i repartitioned my hdd to install ubuntu, and i don't feel like i have enough space on my windows partition. i want to uninstall ubuntu, delete the ubuntu partition, and have my one big hdd again for windows. i have no idea how to do this, and i dont have a vista disk.

after i get that accomplished, i'd like some links or info or what have you on how to install ubuntu onto my 500gig external hdd. i welcome all input, but please don't tell me to try anything that may jeopardize my data. thanks guys.

---

### Post by confused57 on 2007-08-10
> **superjeff said:**
> i'm dual booting ubuntu and vista home premium on a single 120 gig hdd, and i repartitioned my hdd to install ubuntu, and i don't feel like i have enough space on my windows partition. i want to uninstall ubuntu, delete the ubuntu partition, and have my one big hdd again for windows. i have no idea how to do this, and i dont have a vista disk.

after i get that accomplished, i'd like some links or info or what have you on how to install ubuntu onto my 500gig external hdd. i welcome all input, but please don't tell me to try anything that may jeopardize my data. thanks guys.
Since you don't have a vista disk, you might be able to use MbrFix.exe to restore your Vista IPL to the mbr:
[http://ubuntuforums.org/showpost.php?p=2809942&postcount=22](http://ubuntuforums.org/showpost.php?p=2809942&postcount=22)
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Here's a link for installing on an external hard drive:
[http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external)

You "might" be able to do a regular  install of Ubuntu...set your external hard drive to boot before your internal hard drive in bios, before you boot up the live cd to install.  When you reach the screen to install grub, you could click on the "Advanced" button and you can type in the hard drive where you want grub installed, e.g. /dev/sdb(or however your external drive is recognized by the installer).

---

### Post by jenson on 2007-08-10
> **confused57 said:**
> Since you don't have a vista disk, you might be able to use MbrFix.exe to restore your Vista IPL to the mbr:
[http://ubuntuforums.org/showpost.php?p=2809942&postcount=22](http://ubuntuforums.org/showpost.php?p=2809942&postcount=22)
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Here's a link for installing on an external hard drive:
[http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external)

You "might" be able to do a regular  install of Ubuntu...set your external hard drive to boot before your internal hard drive in bios, before you boot up the live cd to install.  When you reach the screen to install grub, you could click on the "Advanced" button and you can type in the hard drive where you want grub installed, e.g. /dev/sdb(or however your external drive is recognized by the installer).

Hi confused57,

Does that mean we can install Ubuntu on a removable external hard disk which is plug-and-play? So when I'm not using my Ubuntu, I simple unplug the external hard disk from my laptop/PC by just plugging out the USB cable? Do you mean that?

Sorry I'm newbie, so my questions might sound stupid to you.

Thanks.

Regards,
Jenson

---

### Post by confused57 on 2007-08-10
> **jenson said:**
> Hi confused57,

Does that mean we can install Ubuntu on a removable external hard disk which is plug-and-play? So when I'm not using my Ubuntu, I simple unplug the external hard disk from my laptop/PC by just plugging out the USB cable? Do you mean that?

Sorry I'm newbie, so my questions might sound stupid to you.

Thanks.

Regards,
Jenson

Here is another link for using MbrFix.exe:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
this is for XP, see the other links for Vista

Yes, you "should" be able to install Ubuntu to your external hard drive, if your bios supports booting first to the external drive.  See my other reply for instructions on how to do this, many people make the mistake of installing grub to the internal hard drive's mbr, then they're unable to boot their internal drive with the external drive disconnected.  I believe you have to use the same USB port that the drive was connected to when you installed Ubuntu.  There are numerous threads in the forum of users who have successfully installed to an external hard drive.  If at all possible, it would probably be best to install Ubuntu near the beginning of the hard drive to avoid any possible problems with a large hard drive.

---

### Post by superjeff on 2007-08-10
confused57, you're the man. i think your info is gonna get me exactly where you need to be, but i have one problem:

**C:\> MbrFix /drive 0 fixmbr /yes**

that gives me this error:
**Functon failed. Error 5: Access is denied.**

i don't understand this because i am the administrator, i'm the only user on this computer. mbrfix is exactly what i need if i can get it to work. thanks a lot for the help so far.

---

### Post by superjeff on 2007-08-10
oh, and if i only have one hard drive, my hard drive is drive 0, right?

---

### Post by superjeff on 2007-08-10
alright, i think i fixed my mbr with supergrub. i boot straight into windows no questions asked. now when i boot with my livecd, i get to the ubuntu menu, but i don't know which option to pick to boot into ubuntu. the only options are the text installers, memory test, cd test, boot from 1st hard drive...nothing that sounds like boot to ubuntu. if i can uninstall ubuntu in windows, that'd be best.

---

### Post by confused57 on 2007-08-10
> **superjeff said:**
> alright, i think i fixed my mbr with supergrub. i boot straight into windows no questions asked. now when i boot with my livecd, i get to the ubuntu menu, but i don't know which option to pick to boot into ubuntu. the only options are the text installers, memory test, cd test, boot from 1st hard drive...nothing that sounds like boot to ubuntu. if i can uninstall ubuntu in windows, that'd be best.

Glad you were able to get your mbr restored...wasn't sure if SGD could restore Vista's IPL.  You should be able to use Vista's "Disk Manager" to delete your Ubuntu partitions and resize your Vista partition:
[http://www.pro-networks.org/forum/viewstory.php?t=78111](http://www.pro-networks.org/forum/viewstory.php?t=78111)

If you need to boot into Ubuntu for some reason, there are some instructions on this site for doing a direct kernel boot into your Ubuntu installation:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by superjeff on 2007-08-11
you're the man, confused. many thanks to you for helping me.

---

### Post by jenson on 2007-08-12
> **confused57 said:**
> Here is another link for using MbrFix.exe:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
this is for XP, see the other links for Vista

Yes, you "should" be able to install Ubuntu to your external hard drive, if your bios supports booting first to the external drive.  See my other reply for instructions on how to do this, many people make the mistake of installing grub to the internal hard drive's mbr, then they're unable to boot their internal drive with the external drive disconnected.  I believe you have to use the same USB port that the drive was connected to when you installed Ubuntu.  There are numerous threads in the forum of users who have successfully installed to an external hard drive.  If at all possible, it would probably be best to install Ubuntu near the beginning of the hard drive to avoid any possible problems with a large hard drive.

Hi confused57,

You definitely rock! Thanks for the reply. I think this is the first time I know I can install Ubuntu onto external Hard drive. In fact, I hope to move my WinXP to external drive more than Ubuntu, as I'm using Ubuntu more now, hehe, thus I don't wish to slow down the loading or running speed of my Ubuntu. XP is now mainly for gaming and some programming work.

Regards,
Jenson

---

