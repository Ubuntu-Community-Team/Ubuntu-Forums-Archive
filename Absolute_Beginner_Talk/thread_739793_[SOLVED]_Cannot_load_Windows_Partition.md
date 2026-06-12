---
title: "[SOLVED] Cannot load Windows Partition"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by dapps2k on 2008-03-30
Earlier today I was trying to partition my drive in Ubuntu when it failed in the middle and then locked up.  From another user's suggestion, I decided to try the installation again, overwriting some miscellaneous media files and a couple game installation directories to finally install Ubuntu.

However, when grub saw Windows XP, it only leads me to the factory-restore partition, which would erase all of my data (NOT what I would want to happen).  My friend tinkered around with the menu.lst and was able to get it to do something, but now it just says Error: 12, Invalid Device Requested.  

Is there any way for me to save my Windows partition?

Here is my fdisk -l output.  I believe my Windows partition should be sda5.
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2             638       15487   119282625    f  W95 Ext'd (LBA)
/dev/sda3           15488       15609      979965   82  Linux swap / Solaris
/dev/sda4   *       15610       30401   118816740   83  Linux
/dev/sda5             638       15487   119282593+   7  HPFS/NTFS

```

---

### Post by apothecaryaaron on 2008-03-30
First, does Ubuntu boot correctly? If so, you can mount the Windows partition, and burn a CD(s) of the important data. That way you don't lose anything important no matter what.
 
As far as grub errors, I think I've seen some threads on that one. I'll look for them and link them.
 
EDIT:  Can you post your /boot/grub/menu.lst ?  It may be as easy as changing the "root" of the Windows choice.

---

### Post by Oldsoldier2003 on 2008-03-30
> **dapps2k said:**
> Earlier today I was trying to partition my drive in Ubuntu when it failed in the middle and then locked up.  From another user's suggestion, I decided to try the installation again, overwriting some miscellaneous media files and a couple game installation directories to finally install Ubuntu.

However, when grub saw Windows XP, it only leads me to the factory-restore partition, which would erase all of my data (NOT what I would want to happen).  My friend tinkered around with the menu.lst and was able to get it to do something, but now it just says Error: 12, Invalid Device Requested.  

Is there any way for me to save my Windows partition?

Here is my fdisk -l output.  I believe my Windows partition should be sda5.
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2             638       15487   119282625    f  W95 Ext'd (LBA)
/dev/sda3           15488       15609      979965   82  Linux swap / Solaris
/dev/sda4   *       15610       30401   118816740   83  Linux
/dev/sda5             638       15487   119282593+   7  HPFS/NTFS

```
Download and burn a  [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/"), Boot from the cd and have it replace grub. it should find your Xp installation and set up menu.lst properly. Its a lot easier than manually fixing the problem, though if you post your menu.lst we can help you sort it out that way too...

---

### Post by dapps2k on 2008-03-30
Yep, thankfully Ubuntu does work so I can post this message. :D

Ubuntu also is able to see my Windows partition.  However, I lack any external memory devices to back up my memory, which is why I'm trying to save my Windows partition.

Here's my menu.lst:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9ae62fe1-557e-4742-867a-1530f4f6452c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9ae62fe1-557e-4742-867a-1530f4f6452c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

---

### Post by apothecaryaaron on 2008-03-30
> **Oldsoldier2003 said:**
> Download and burn a [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/"), ...
 
I see SuperGrub recommended quite often, but I have never used it.  From what I understand, it's much easier than what I was about to get us into.  I'd try that route first, you can always reinstall the old grub and manual edit if SuperGrub doesn't work.

---

### Post by dapps2k on 2008-03-30
Alright, I'll give that shot tomorrow.  I'll post an update if anything happens.

---

### Post by apothecaryaaron on 2008-03-30
> **dapps2k said:**
> 
Here's my menu.lst:

 
Wow, I thought I was gonna get that reply in first. It may be as easy as changing your Windows "root" line to 
 
rootnoverify (hd0,4)
or (hd0,1) or (hd0,2)
 
It depends on where your Windows bootloader was installed at. It could be on "Compaq diagnostics" or "W95 Ext'd (LBA)," and that could be why you get error 12 when it tries to boot straight to Windows.
 
EDIT:  Ah!  Now I feel slow...twice in one thread.   Keep us updated and Good luck.
As far as backup goes, I like to email myself all of my smaller, but important, files.  Gmail works well as temporary storage.

---

### Post by dapps2k on 2008-03-30
> It may be as easy as changing your Windows "root" line to

rootnoverify (hd0,4)
or (hd0,1) or (hd0,2)

I tried your suggestion, but that unfortunately didn't change things; it still shows Error 12: Invalid Device Requested.

I also tried using Super Grub.  I tried to boot Windows from it, but it only booted up my computer's factory reset partition, which again would erase everything from my drive (not what I would want to happen).  Trying to load the partition directly only caused Super Grub to restart.  So I guess that means my Windows installation is hosed.

Well, at least I have Ubuntu still to back up my data.  A couple questions before I reinstall Windows: How can I get Ubuntu to write/read NTFS files so I can backup my data?  And if I reinstall Windows, would that overwrite Grub?  How would I fix that if Windows did indeed overwrite Grub?

---

### Post by FreewareFan on 2008-03-30
Have you tried booting from your Windows install disc, and choosing Repair?  Then when you are in the Repair section, type fixmbr   to repair the original master boot record.  That should get you back into windows, if it hasn't been damaged.   From that point, you could use SuperGrub to install another grub that should let you boot into both windows and ubuntu.

---

### Post by collinp on 2008-03-30
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,4)
savedefault
makeactive
chainloader    +1

Try changing the (hd0,4) to (hd0,5). Idk if that will work, it was just a educated guess.

---

### Post by apothecaryaaron on 2008-03-30
> **dapps2k said:**
> How can I get Ubuntu to write/read NTFS files so I can backup my data?
 
Somebody please correct me if I'm wrong, but Ubuntu is ok reading from NTFS filesystems, it just sometimes has trouble writing back onto one.  My personal experience is that you can copy files from the Windows partition without doing anything special, and I've written stuff back to Windows as well, although I was told it was risking file corruption.

---

### Post by dapps2k on 2008-03-31
> Somebody please correct me if I'm wrong, but Ubuntu is ok reading from NTFS filesystems, it just sometimes has trouble writing back onto one. My personal experience is that you can copy files from the Windows partition without doing anything special, and I've written stuff back to Windows as well, although I was told it was risking file corruption.

I think you're right.  I was able to back up my data to my friend's hard drive after I found out that 7.10 (Gutsy Gibbon) should already be able to read/write NTFS partitions.  I apparently was reading about older versions of Ubuntu which did not have that capability.

I just reinstalled Windows and now both OSes run perfectly fine.  I want to thank everyone for helping me out, even if nothing came out the way I wanted.

---

