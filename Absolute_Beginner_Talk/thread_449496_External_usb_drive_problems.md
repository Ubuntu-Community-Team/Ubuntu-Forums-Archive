---
title: "External usb drive problems"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by penguinjar on 2007-05-20
I have a laptop which runs XP, and I attempted to install Ubuntu on an external usb drive.  I got it installed, but now I just get some grub error and I can't boot into either operating system.  After searching here for answers,  I realized I can't boot from a usb drive, so now I'm abandoning that plan and I want to install Ubuntu on the internal drive along with XP.  However, I fear I will lose all my XP stuff in the process, so I want to copy some stuff to the external drive first.  Right now I'm using the Live CD because I can't boot into win or linux, and I can see all of my windows files on the internal drive, but it won't let me copy any of them to the external drive because it says I don't have the permissions. 

So in summary, how can I copy files from my internal XP drive to my external drive while booted on the Live CD?  And how should I format the external drive to make this work?

Thanks

---

### Post by taurus on 2007-05-20
<Alt>F2 -> gksudo nautilus

And you can format that external harddrive to fat32/vfat if you want to share it with Ubuntu and Windows.

---

### Post by Happy_Man on 2007-05-20
Just one question: couldn't you boot the XP down there in the internal, copy whatever over, and then install from the LiveCD? Oh wait, you stuck GRUB on, nvm. Right, go ahead and open a terminal (Applications --> Accessories --> Terminal) and type this in:

```
sudo fdisk -l
```

That will show us how Ubuntu sees the hard drives attached to the laptop, makes entering the next set of commands easier... also, if you installed to an external drive, doesn't that mean that it's already ext3 formatted? If so, good; you won't need to reformat it, maybe just erase it.

EDIT: also, if you have files over 4 GB, FAT32 won't store them. There are ext3 drivers available for Windows at the site [http://fs-driver.org](http://fs-driver.org).

---

### Post by starcraft.man on 2007-05-20
I'm sure taurus answered your question, just wanted to point out in future if you plan to mess around with partitions and OS on different drives and want to make sure you always have a failsafe in case this happens again, keep a copy of [GAG]("http://gag.sourceforge.net/") nearby. It is good, and will always let you boot an OS, unless you corrupted it... its also super simple to get working.

---

### Post by Happy_Man on 2007-05-20
> **starcraft.man said:**
> I'm sure taurus answered your question, just wanted to point out in future if you plan to mess around with partitions and OS on different drives and want to make sure you always have a failsafe in case this happens again, keep a copy of [GAG]("http://gag.sourceforge.net/") nearby. It is good, and will always let you boot an OS, unless you corrupted it... its also super simple to get working.

So GAG replaces GRUB?

---

### Post by starcraft.man on 2007-05-20
> **Happy_Man said:**
> So GAG replaces GRUB?

Yes it does replace GRUB, its an alternative bootloader, very good from everything I've seen. It very easily detects and allows for booting of any OS you have on drives the BIOS can see. I recommend it usually for emergencies and getting back into your OS when GRUB is giving lots of trouble, then I'd have them restore GRUB via the terminal, I prefer it for daily use.

---

