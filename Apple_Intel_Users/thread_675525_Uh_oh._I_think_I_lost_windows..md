---
title: "Uh oh. I think I lost windows."
date: 2008-01-22
forum: Apple Intel Users
---

### Post by smocksturr on 2008-01-22
Okay, so.  On my Macbook C2D I have Leopard installed, also Windows XP.
Decided to put Feisty on as well.
So I installed rEFIt, works great, was able to boot everything.
Installed Feisty from livecd to 9 gigs at end of drive, except near the end of partitioning, I set the bootloader to hd(0,2) instead of hd(0) 
[i read that in a guide somewhere else, can't remember why.]
so now, rEFIt sees Linux and Mac, both which boot fine.  However, Windows is still on there somewhere.  I can explore the disk in both OSes but I cannot boot from it.
When I boot into Ubuntu, GRUB offers me the option to boot to Windows XP, but if i pick it, it boots me right back to the GRUB menu again.
If i grab my Windows CD and use the fixmbr command, will that help anything?

---

### Post by cyberdork33 on 2008-01-22
> **smocksturr said:**
> If i grab my Windows CD and use the fixmbr command, will that help anything?

Possibly. You need to post details about your partitioning though, because, from what i understand of your situation, (hd0,2) would be he windows partition, not your Ubuntu partition.

---

### Post by smocksturr on 2008-01-22
Okay, did some scouting.
My drive is set up like so:
sda1: EFI boot (200 megs)
sda2: Mac OSX (80 gigs ish)
sda3: Windows (15 gigs or so)
sda4: Ubuntu (oh, say, 9 gigs ish)
sda5: swap (a gig or so)

If I installed the bootloader to hd(0,2), what does that mean?
Also, rEFIt is gone again. seems like it only stays for a few minutes before it succumbs to Boot Camp and Apple's EFI.
So, now, when I boot up while holding option, I get Windows or Mac.
Choosing windows, I get GRUB. Cool, I'd actually like it this way if it worked.
Still, selecting Windows from the GRUB bootlist does not boot windows, it boots back into GRUB.
What do I do?

---

### Post by ronocdh on 2008-01-22
> **smocksturr said:**
> Okay, did some scouting.
My drive is set up like so:
sda1: EFI boot (200 megs)
sda2: Mac OSX (80 gigs ish)
sda3: Windows (15 gigs or so)
sda4: Ubuntu (oh, say, 9 gigs ish)
sda5: swap (a gig or so)

If I installed the bootloader to hd(0,2), what does that mean?
Also, rEFIt is gone again. seems like it only stays for a few minutes before it succumbs to Boot Camp and Apple's EFI.
So, now, when I boot up while holding option, I get Windows or Mac.
Choosing windows, I get GRUB. Cool, I'd actually like it this way if it worked.
Still, selecting Windows from the GRUB bootlist does not boot windows, it boots back into GRUB.
What do I do?
Can you confirm the existence of your Windows partition (meaning it wasn't overwritten by Ubuntu) by browsing its files from OS X? If so, it is indeed still there, and you should just need to reinstall GRUB. It will autodetect Windows and on a reboot, the GRUB screen should work for you.

---

### Post by cyberdork33 on 2008-01-23
> **smocksturr said:**
> Okay, did some scouting.
My drive is set up like so:
sda1: EFI boot (200 megs)
sda2: Mac OSX (80 gigs ish)
sda3: Windows (15 gigs or so)
sda4: Ubuntu (oh, say, 9 gigs ish)
sda5: swap (a gig or so)

If I installed the bootloader to hd(0,2), what does that mean?
well, that would be partition 3, which is your windows partition. So if you installed to that partition, I would guess that it overwrote some information that windows needs to boot up. You will probably need to run the recovery console from the windows disk, and repair the bootsector. (use the fixboot command)

> Also, rEFIt is gone again. seems like it only stays for a few minutes before it succumbs to Boot Camp and Apple's EFI.eh, just need to reinstall in osx. 
> So, now, when I boot up while holding option, I get Windows or Mac.
Choosing windows, I get GRUB. Cool, I'd actually like it this way if it worked.
Well, if you really want to go through two menus... (refit then grub) that is very easy to do as that is the default way to install. This was a problem for a lot of people since the keyboard doesn't work in grub for many... (including myself).

> Still, selecting Windows from the GRUB bootlist does not boot windows, it boots back into GRUB.that's because you installed grub to the bootsector of the windows partition, so you are literally selecting to boot grub... Use the FIXBOOT command on the windows partition and you should be ok (though you might also need to install grub to the MBR afterwards (hd0)

---

### Post by smocksturr on 2008-01-23
Okay, how do I go about installing GRUB?
Something just went wrong in my OSX install and I had to restore from a 3 month old Tiger backup... Hope that didn't have anything to do with me effing around with the boot sectors and such.
Anyways, since I'm practically there already, I'd love to finish this up.
So, run FIXBOOT from the Windows disk and then reinstall GRUB?
How do I go about doing that.

---

### Post by smocksturr on 2008-01-23
Hey, cool.  Just wrote a new bootsector to the Win partition, and now it gives me a Disk Error: Press any key to restart error.
Never even seen that, is that GRUB?
Whatev, I've got a 3 month old windows backup too.
If i straight up restore my backed up partition to the one on my disk, will Windows start?
and if that works, then I just have to figure out how to get GRUB to work again?

---

### Post by ronocdh on 2008-01-23
> **cyberdork33 said:**
> Well, if you really want to go through two menus... (refit then grub) that is very easy to do as that is the default way to install. This was a problem for a lot of people since the keyboard doesn't work in grub for many... (including myself).
Is this still the case for you? IIRC there was an Apple EFI update in September 2007 that completely resolved this issue for me. My keyboard has since been 100% responsive on the GRUB screen as well as on LiveCD menus before loading the Linux kernel.

---

### Post by ronocdh on 2008-01-23
> **smocksturr said:**
> Hey, cool.  Just wrote a new bootsector to the Win partition, and now it gives me a Disk Error: Press any key to restart error.
Never even seen that, is that GRUB?
Whatev, I've got a 3 month old windows backup too.
If i straight up restore my backed up partition to the one on my disk, will Windows start?
and if that works, then I just have to figure out how to get GRUB to work again?
It sounds to me like you've only changed the boot sector and not the contents of the filesystem or partitions, so don't bother with a restore. You just need to get GRUB working and you're fine. 

So FIXMBR from the WinXP CD didn't get you back in order? Try from a live CD:
```
sudo grub
find /boot/grub/stage1      #output will be used in next command
root (hdx,y)         #where x and y are the values given by the "find" command
setup (hdx)
quit
reboot
```
Another method is **sudo grub-install [device name]** which might work fine for you too. I don't really know which is the preferred method. Most people I know use grub-install, but most guides on the internet I've seen use the method I've typed out.

---

### Post by bwtranch on 2008-01-23
Might try fdisk

There is a good tutorial on the Gentoo website about partitioning as well.

---

### Post by bwtranch on 2008-01-23
yOU SHOULD BACK UP YOUR FILES BEFORE YOU DO THIS THOUGH.

There is a good tutorial using tar here:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

There are many other ways, but this is simple. I keep a backup on my server and on CD. You really don't have to backup all that. Usually just where you keep your important files like /user/home

Hopes this helps.

---

### Post by smocksturr on 2008-01-23
Well, I just formatted the windows partition anyways. nothing important on it anyways.
i'm going to restore the windows partition and then take things from there.
Hey, question. Since I'm doing this all, What if I just nuked the Linux part and swap part, and reinstalled completely?
Would that fix my errors?
If i were to do that, what exactly are my special install steps?

---

### Post by ronocdh on 2008-01-23
> **smocksturr said:**
> Well, I just formatted the windows partition anyways. nothing important on it anyways.
i'm going to restore the windows partition and then take things from there.
Hey, question. Since I'm doing this all, What if I just nuked the Linux part and swap part, and reinstalled completely?
Would that fix my errors?
If i were to do that, what exactly are my special install steps?
I think most triple boot guides recommend you install Windows before you install Ubuntu. This way GRUB will recognize XP and hopefully leave you with an error-free bootloading process (although you will have to chainload if you're using rEFIt and GRUB).

---

### Post by smocksturr on 2008-01-23
See, I have a backup of my windows part on an external drive.
Can I use that instead of installing Windows?
Right now I just restored the windows partition and tried to install ubuntu again fresh, keeping the boot sector at default (hd0 i guess?)
unforunately, now nothing works.
Any way I can restore my bootsector without restoring my Mac partition?

---

### Post by smocksturr on 2008-01-23
Also, here's the partition report.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    182861863  Mac OS X HFS+
 3      182867895    219287249  EFI System (FAT)
 4      221355677    234441614  Basic Data
 5      219287317    221355676  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    182861863  af  Mac OS X HFS+
 3 *            1    219287249  ee  EFI Protective
 4      221355677    234441614  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 182867895:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 3, type EFI System (FAT)

Partition at LBA 221355677:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 219287317:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by smocksturr on 2008-01-23
Sorry to be bumping so much, the situation just keeps changing.
Thanks also for all your help, you guys are fantastic.

Okay, so, I ran a live cd and reinstalled grub.
Cool, I get the option to boot linux in REFIT now. when i select it, I get grub.
linux boots from grub, cool.
when i select Windows in GRUB, i get the "Non-system disk" error again.
Hm.
What should I do to get the windows partition back on its feet?
Restore it yet again?
Or would a Fixboot or Fixmbr work?

---

### Post by cyberdork33 on 2008-01-23
> **ronocdh said:**
> So FIXMBR from the WinXP CD didn't get you back in order?FIXMBR is a different command. It will overwrite the boot[U]loader.
[/U]FIXBOOT will fix the boot_sector_ on the particular partition (that he likely overwrote by attempting to install grub to the windows partition).

> **bwtranch said:**
> Might try fdisk.Fdisk is a dangerous animal on a GPT disk. I would suggest only using derivatives of parted.

> **smocksturr said:**
> Hey, question. Since I'm doing this all, What if I just nuked the Linux part and swap part, and reinstalled completely?That is sounding like the best idea if you have backups of everything.

> **smocksturr said:**
> Okay, so, I ran a live cd and reinstalled grub.
Cool, I get the option to boot linux in REFIT now. when i select it, I get grub.
linux boots from grub, cool.
when i select Windows in GRUB, i get the "Non-system disk" error again.
Hm.
What should I do to get the windows partition back on its feet?
Restore it yet again?
Or would a Fixboot or Fixmbr work?Well that seems to be an improvement... I am not sure how to fix your windows partition. It is acting like there are some system files missing (that windows needs to have). The "Non-system disk" error is a windows error message I think. From what I just found on the net, that error is because of a bad bootsector or a damaged MBR (but we know the MBR is good, becuase grub is installed there, so, I would try the FIXBOOT command again... but You might want to make sure you are using it correctly, and it sounds like the last time you used it, it messed up the OSX partition. You can use the MAP command to get the partitions and the letter it is seeing them as. There is more information about the recovery console commands here:
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by cyberdork33 on 2008-01-23
> **ronocdh said:**
> Is this still the case for you? IIRC there was an Apple EFI update in September 2007 that completely resolved this issue for me. My keyboard has since been 100% responsive on the GRUB screen as well as on LiveCD menus before loading the Linux kernel.Yes, yes. It was fixed for awhile, but it broke again. You can read my torment starting here:
[http://ubuntuforums.org/showpost.php?p=3453879&postcount=7](http://ubuntuforums.org/showpost.php?p=3453879&postcount=7)

---

### Post by cyberdork33 on 2008-01-23
> **ronocdh said:**
> Is this still the case for you? IIRC there was an Apple EFI update in September 2007 that completely resolved this issue for me. My keyboard has since been 100% responsive on the GRUB screen as well as on LiveCD menus before loading the Linux kernel.Yes, yes. It was fixed for awhile, but it broke again. You can read my torment starting here:
[http://ubuntuforums.org/showpost.php?p=3453879&postcount=7](http://ubuntuforums.org/showpost.php?p=3453879&postcount=7)
I think it may have been related to me updating to Leopard, although i have no idea how...

Interestingly, I found that it works ok with my bluetooth Apple keyboard, but not the USB one... I would expect the opposite.

---

### Post by smocksturr on 2008-01-23
Alright, so I deleted my Windows partition and restored it from my backed up one.
HOWEVER
i just realized that at a time I had tried to install Ubuntu on my external drive, which somehow ended up with me no longer being able to boot from my backup Windows partition.
So in a little while I will try to use FIXBOOT on my windows partition.
If now, I'll just get my hands on another XP disc and install it, then reinstall GRUB.
That sounds to me like it would work.

---

### Post by cyberdork33 on 2008-01-23
> **smocksturr said:**
> Alright, so I deleted my Windows partition and restored it from my backed up one.
HOWEVER
i just realized that at a time I had tried to install Ubuntu on my external drive, which somehow ended up with me no longer being able to boot from my backup Windows partition.
So in a little while I will try to use FIXBOOT on my windows partition.
If now, I'll just get my hands on another XP disc and install it, then reinstall GRUB.
That sounds to me like it would work.you don't need to reinstall grub, you just said that it was working fine in your last post.

---

### Post by smocksturr on 2008-01-23
Oh, right.
So if i just reinstall windows GRUB will recognize it the same?

---

### Post by cyberdork33 on 2008-01-23
> **smocksturr said:**
> Oh, right.
So if i just reinstall windows GRUB will recognize it the same?
You will have to add an entry for windows, as that is usually done via the installer.


Just add a Windows Entry at the bottom of your menu.lst:
```
title=Windows
rootnoverify (hd0,5)
makeactive
chainloader +1
```NOTE: change the (hd0,5) to the right partition for you!

---

### Post by smocksturr on 2008-01-23
ARGH.
okay, so.
i installed windows again and resynced the tables using rEFIt.
windows gives me a hal.dll error and won't boot.
SO.
i booted my gparted livecd and tossed both windows and linux partitions. gone.
Where can I find a good Feisty 7.04 triple boot guide? I don't want to eff with my OSX install seeming that it's finally functional again.

---

