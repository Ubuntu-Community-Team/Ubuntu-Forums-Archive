---
title: "Dual boot xp and ubuntu"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by mural on 2007-01-10
I am trying to dual boot xp and edgy.  I have two separate SATA hard drives.  One has XP and the other has Ubuntu Edgy.  Upon powering up, XP gets loaded by default.  I do not see GRUB.   How can make GRUB the default loader?

---

### Post by darkcyber on 2007-01-10
> **mural said:**
> I am trying to dual boot xp and edgy.  I have two separate SATA hard drives.  One has XP and the other has Ubuntu Edgy.  Upon powering up, XP gets loaded by default.  I do not see GRUB.   How can make GRUB the default loader?

I'm curious to see how you get this accomplished.  I'm having a real tuff time installing to a SATA hd.  I have 1 SATA and 2 IDE's and I'm having a similar problem.

---

### Post by mural on 2007-01-10
Installing Ubuntu onto the SATA was no problem.  I first installed XP on one hdd and then installed Ubuntu on the second hdd, thinking that when I power up, GRUB will give me the choice of selecting which OS I wanted to boot.  But that is not happening.  I can boot into Ubuntu however by going into the BIOS and selecting the hdd which has Ubuntu installed on it.  Once I do that, GRUB gives me the option of selecting Ubuntu or XP.  But I do not want to go into the BIOS every time I want to boot Ubuntu.  Any suggestions?

---

### Post by jimrz on 2007-01-10
> **mural said:**
> I am trying to dual boot xp and edgy.  I have two separate SATA hard drives.  One has XP and the other has Ubuntu Edgy.  Upon powering up, XP gets loaded by default.  I do not see GRUB.   How can make GRUB the default loader?

I, too, initially had trouble due to issues with SATA2 +  and the RAID BIOS on my machine. After several unsuccessful attempts, I finally wound up removing my win drive / connecting the ubuntu drive to SATA0 (my bios would not accept any other for a single drive install) / ran the install (went perfectly) / put the win drive back (SATA3) and all is well. Also, rather than adding the win drive to GRUB I simply, on the rare ocassions that I boot to win anymore, I just go into setup (f12, in my case) and manually select the win drive to boot to. So I wound up with kind of a quasi-dual boot setup, but it works just fine for me.

---

### Post by bodhi.zazen on 2007-01-10
It seems you need to install grub to the MBR of the first HD:

[http://www.ubuntuforums.org/showpost.php?&p=1781796&postcount=2](http://www.ubuntuforums.org/showpost.php?&p=1781796&postcount=2)

In your case, assuming your ubuntu root partition is on the first partition of the second drive, at the grub boot prompt type:

> root (hd1,0)
setup (hd0)
quit

HTH

Reference: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by jimrz on 2007-01-11
> **bodhi.zazen said:**
> It seems you need to install grub to the MBR of the first HD:

[http://www.ubuntuforums.org/showpost.php?&p=1781796&postcount=2](http://www.ubuntuforums.org/showpost.php?&p=1781796&postcount=2)

In your case, assuming your ubuntu root partition is on the first partition of the second drive, at the grub boot prompt type:



HTH

Reference: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

that is one of the methods I used that did not work because the BIOS did not want to play. had to go the route listed above.

---

### Post by bodhi.zazen on 2007-01-11
> **jimrz said:**
> that is one of the methods I used that did not work because the BIOS did not want to play. had to go the route listed above.

I hate it when that happens.

BIOS can be a drag for sure.

Is there an update for your BIOS ? I've been lucky with BIOS updates if available.

Otherwise, did you try using map ?

From the guide I posted:

'map' commands sometimes need to be added when Windows is installed on a non-first hard disk. For example,

```
title      Microsoft Windows 98SE
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

I do not know if the map option will help you ??

---

### Post by rabid emu on 2007-01-11
Try setting the BIOS to boot to your second HD by default.  That way you can load grub on that HD and tell it to boot to the first HD when you want to run Windows.  I don't know if it'll work but give it a try.

---

### Post by jimrz on 2007-01-11
> **bodhi.zazen said:**
> I hate it when that happens.

BIOS can be a drag for sure.

Is there an update for your BIOS ? I've been lucky with BIOS updates if available.

Otherwise, did you try using map ?

From the guide I posted:

'map' commands sometimes need to be added when Windows is installed on a non-first hard disk. For example,

```
title      Microsoft Windows 98SE
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

I do not know if the map option will help you ??

thanks ... no BIOS update available ... no problem really, as infrequently as I actually have to boot into xp I'm fine with the setup as described ... was just passing along info in case it might prove useful to the OP

rabid emu- thanks for the suggestion ... might work but think I'll just leave it as is for the reason stated above

---

### Post by mural on 2007-01-13
Hello All,

Sorry for the delay in replying.  Thank you all for your inputs and suggestions.  I tried all of your suggestions but no luck.  I ended up messing up my MBR and could not boot anything at all.  After some research I figured out how to "dual boot xp and ubuntu".  Note that I did not have to reinstall Xp, only Ubuntu but that was no big deal. This is what I did to fix my problem.

I have two sata connectors.SATA 0_1 and SATA 2_3.

My previous (wrong) configuration was like this:
SATA 0 had hard drive with Ubuntu
SATA 2 had hard drive with Xp.

My current configuration is like this:
SATA 0 had hard drive with Xp.
SATA 2 had hard drive with Ubuntu.


After doing this, I used Xp's installation cd to fix my MBR. Then I made sure that I was able to boot into Xp. 
All was fine.  Then installed ubuntu onto the second hard drive and made sure that GRUB was installed to (hd0).

Now all is fine.  When I boot up, GRUB gives me the option to select whcih OS I want to boot. This is how my menu.lst looks now:

-----------------------------------------------------------------------------

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
---------------------------------------------------------------------------------------

So the lesson that I learnt is to make sure that Xp is installed on the primary sata connector and then install ubuntu on anyother available connector.

Hope that this helps others.

---

