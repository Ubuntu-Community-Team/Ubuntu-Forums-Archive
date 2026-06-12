---
title: "No boot to hard drive after install"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by ksujason on 2008-01-05
I installed ubuntu last night and the it went on flawlessly. After starting the reboot and removing the cd I went into bios and changed the boot order back to the hard disk. Even though I did this, it still tries to boot to the CD first and will then give a disk boot failure.
I can go back into bios and my settings are still set to hard drive first.
Thanks for any suggestions.

---

### Post by overdrank on 2008-01-05
> **ksujason said:**
> I installed ubuntu last night and the it went on flawlessly. After starting the reboot and removing the cd I went into bios and changed the boot order back to the hard disk. Even though I did this, it still tries to boot to the CD first and will then give a disk boot failure.
I can go back into bios and my settings are still set to hard drive first.
Thanks for any suggestions.

Hi and welcome, you can use this thread to install the reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

---

### Post by skymera on 2008-01-05
nothing at all loads?

ok, try reinstalling the grub menum, i had to with my lappytop.

once in live cd open up the terminal and type

```

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)

RESTART

```

is that dosent work get the Super Grub Disk.]
its a super hero in disguise :wink:

---

### Post by ubutufan on 2008-01-05
To begin with it does not make any difference if you changed the boot order. As long as you have no  cd in the device, the boot up process will jump from one device to another trying to locate a bootable partition.
Which brings us to this situation you are describing. I suggest you reinsert the ubuntu livecd and use partition editor to post the results here. we cannot help if we have no details.
Alternatively you may download GPARTED, burn it and use this livecd to examine your partitions.
In any event we need information

---

### Post by ksujason on 2008-01-05
Thanks for all of the suggestions. I tried all of the above and it still tries to boot to the CD. 
How do I go about posting the results of the partition manager?
Sorry for all of the questions, but I am very new to umbuntu.

Thanks again for all your help.

---

