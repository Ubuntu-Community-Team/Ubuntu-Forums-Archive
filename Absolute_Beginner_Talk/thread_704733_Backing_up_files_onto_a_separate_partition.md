---
title: "Backing up files onto a separate partition"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by sparticus06 on 2008-02-22
I am currently duel booting windows and ubuntu but I want o give Kubuntu a try for the hell of it. I want to just reformat the whole hard drive and just have kubuntu. All that is easy, but, I want to backup some music and picture files and I don't have a backup device.

I was thinking of saving all the things I want backupped onto a different partition. 

Here is my fdisk information

> Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x412d412d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hdc2            5100        5161      498015   82  Linux swap / Solaris
/dev/hdc3            5162        5167       48195   83  Linux
/dev/hdc4            5168        9964    38531902+  83  Linux


Thanks!

---

### Post by Crooksey on 2008-02-22
```

$ sudo apt-get install kubuntu-desktop
```

No need to reinstall.

---

### Post by sparticus06 on 2008-02-22
> **Crooksey said:**
> ```

$ sudo apt-get install kubuntu-desktop
```

No need to reinstall.

Simple enough! Thanks! Will I be able to switch between Gnome and kde or no?

---

### Post by Crooksey on 2008-02-22
Yes, just press the "session" button from the login manager.

---

### Post by radiocognition on 2008-02-22
> **sparticus06 said:**
> Simple enough! Thanks! Will I be able to switch between Gnome and kde or no?
Maybe a mater of personal taste, but you may prefer to use the 'aptitude' command instead of 'apt-get'.  At least in earlier versions, aptitude did a better job of cleaning up uninstalled programs, libraries, ect,

If you really want to play around in seperate distro's might I recommend using a virtual machine.  I use InnoTek VirtualBox (thats the one that works with my hardware).  It allows you to make a virtual machine where you can play around on whatever OS you want.  You can even link the VM to the hardrive of a seperate install of an operating system, so that within the VM you will be able to boot your windows install.  High system memory is a must though, wouldnt recommend it if you had much less than 1000 MB.

---

