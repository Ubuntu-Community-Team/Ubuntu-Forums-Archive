---
title: "Installing WinXP After Ubuntu"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by jixor on 2007-11-19
I have installed Ubuntu on a machine recently and spent some time customizing it up so I would rather not have to reinstall it however I now want to install windows XP on the machine. The thing if of course I don't want to break Ubuntu or loose the boot loader. So I thought it best to make a post here and see if anyone can point out some instructions or has some good tips. If it helps I have a spare HDD that I could install XP on.

Thanks greatly in advance, Ubuntu very impressive so far! In the future I'll be looking at setting up so I can boot XP in a virtual machine or even see if I can get WINE working well enough.

---

### Post by dpar on 2007-11-19
You will have to reinstall grub, because Windblows will take over the MBR.

---

### Post by wil313 on 2007-11-19
There is, you can partion the disk and install windows on the free partion, but make sure you know which partion is which, other wise you will loose your linux...

---

### Post by wil313 on 2007-11-19
> **dpar said:**
> You will have to reinstall grub, because Windblows will take over the MBR.

And that too... :lol:

---

### Post by jixor on 2007-11-19
No way of repairing the existing ubuntu? Or what if I take out the Ubuntu hdd and put in another to install XP on then swap the Ubuntu hdd back to primary and the XP secondary?

Well I guess its all SATA now so probs primary and seconrady arn't the correct terms but I'm sure you'll ge tthe gist. ;)

---

### Post by dpar on 2007-11-19
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jixor on 2007-11-19
Ah ok so I see, grub is the boot loader. Hmm ok, seems strait forward enough...

---

### Post by jixor on 2007-11-19
I'm actually now considering installing windows onto a USB thumb drive and just putting that in when I want to load windows. Of course there would be an HDD with an NTFS partition on there also for installing apps and etc. I guess this is a little off topic but any thoughts, any reasons why you might expect this to not work, etc?

---

### Post by dpar on 2007-11-19
If your bios is set up to check for a thumb drive first, I don't see why it wouldn't work.

---

