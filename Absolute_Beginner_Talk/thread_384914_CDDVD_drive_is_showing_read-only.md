---
title: "CD/DVD drive is showing read-only"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Eorig on 2007-03-15
win xp with MS virtual pc 07 running ubuntu 6.10.  can't burn says drive is read only

hdparm /dev/hdc

io_support    = 0 (default 16-bit)
unmaskirq     = 0 (off)
using_dma    = 1 (on)
keepsettings = 0 (off)
readonly       = 0 (off)
readahead    = 256 (on)
hdio_getgeo failed:  inappropriate ioctl for device


fstab

/dev/hdc  /media/cdrom0  udf,iso9660 user,noauto 0 0 


device manager list it as virtual cd with the write entries as bool fasle

---

### Post by dstew on 2007-03-15
To burn that disk you need to use a burn program. Most are based on the command line cdrecord. The ordinary linux file system cannot write to CD's.

---

### Post by desyressylence on 2007-03-15
It appears to me like the virtual pc program is telling the operating system that the device is a 'generic' drive without write capabilities.  Especially since it's listed in the device manager as a "virtual cd with write entries as bool false"  Is this something you can change in the virtual pc options?

I'm not familiar with virtual PC though, someone with more experience might have a better idea.

---

### Post by jhenager on 2007-03-15
You'd have to remove XP and the virtual pc part of the equation to see if it is Ubuntu.

---

### Post by Eorig on 2007-03-16
blame mickysoft on that one... all cd/dvd are read-only to guest when using virt pc whither it be win or linux.

no vitual burners lol  ;)

---

### Post by Ecthelion on 2007-03-16
Try VMWare ;-)
Also makes virtual pc's but Ubuntu works fine on it (including the cd-dvd etc)

---

### Post by Eorig on 2007-03-16
i tried vmware server first, moving boxes was jerky as hell so uninstalled it and went to virt pc. not native fast but is close enough so as not dreading to even use it...

---

### Post by Ecthelion on 2007-03-16
> moving boxes was jerky as hell 
..I don't understand what you mean with that...
Moving the virtual machines? Moving...?

I use VMWare a lot to test an auto-install of ubuntu, and to check out unstable releases, and I never had any problem.

---

### Post by Eorig on 2007-03-16
when said boxes meant windows... i.e gedit, term, update mngr, etc.

trying to move a window from one part of the screen to another was very jerky with lag delay stopping after mouse stopped moving. typing was not affected just moving windows around.

there is a little bit of that under virt pc but not nearly to the degree it was under vmware server.

specs: amd 165 OC to 2.7 ghz, 7900gt, 2 gig ram. and i give 512m mem to the virt ubu's

---

