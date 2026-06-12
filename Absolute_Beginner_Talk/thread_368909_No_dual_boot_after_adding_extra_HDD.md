---
title: "No dual boot after adding extra HDD"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by vk99 on 2007-02-23
I had a dual boot setup going with WinXP and Ubuntu 5.10 on a single HDD(40GB), i also run an old 2GB HDD...yesterday i added a 40GB HDD to the existing setup, and now Windows XP fails to boot. On ubuntu under Admin>Disks all three HDDs are listed with their partitions. 
On selecting Windows XP under GRUB menu i get:
Booting &#8216;Microsoft Windows XP Professional&#8217;
root(hd0,0)
Filesystem type unknown, partition type 0×7
savedefault
makeactive
chainloader+1

and then 2 ASCII characters(ASCII 212 & a box like smiley)

The PC is a 2.4GHz PIV, 256MB RAM, Intel 845GVSR Motherboard, both 40GB hard disks are Samsung.

I guess I have the jumper settings on the disks right bcoz all 3 disks are being detected are functional on ubuntu.

Apart from the new harddisk  I have not made any changes to the computer, be it software or hardware.

How can i get winxp to work?

Thanks
Vicky

---

### Post by Kateikyoushi on 2007-02-23
How did you add the drives to the machine ? I mean channels master slaves configs.

What is your partition layout ?

```
sudo fdisk -l
```

---

### Post by vk99 on 2007-02-23
sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1095     8795556    7  HPFS/NTFS
/dev/hda2            2377        4870    20033055    f  W95 Ext'd (LBA)
/dev/hda3            1096        2376    10289632+  83  Linux
/dev/hda5            2436        4870    19559106    b  W95 FAT32
/dev/hda6            2377        2435      473854+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2435    19559106    c  W95 FAT32 (LBA)
/dev/hdb2            2436        4870    19559137+   f  W95 Ext'd (LBA)
/dev/hdb5            2436        4870    19559106    b  W95 FAT32

Disk /dev/hdd: 2113 MB, 2113929216 bytes
64 heads, 63 sectors/track, 1024 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1024     2064352+   b  W95 FAT32

---

### Post by vk99 on 2007-02-23
I have the 40GB HDD with OSs as the Primary master, and the other 40GB as the Primary Slave
My Sony CD-RW drive is the Secondary master, while the 2GB HDD is the secondary slave.

Thanks for helping out Kateikyoushi...any ideas?

---

### Post by vk99 on 2007-02-25
common ppl someones gotta know a way out of this :I

---

### Post by Herman on 2007-02-25
Hello vk99, 
I can't see what the problem could be and you provided very good information.  All I can suggest for the time being is to try one of these Windows XP floppy disks, with a copy of NTLDR, NTdetect and boot.ini on them, they are great! 
These are not your ordinary Windows boot floppy. They bypass most types of problems you might have booting Windows. [How to make your own Windows Xp boot floppy]("http://support.microsoft.com/kb/305595/EN-US/")

Since no-one has been able to spot any problem, it's possible that the problem might be a Windows problem, and might  have something to do with changing your hard disks. I'm hoping if you can get Windows to boot with one of those floppy disks. Maybe it will do a 'found new hardware' or something equally 'Windows-like' and silly, and everything will be fine again. Windows can be a bit finnicky at times, and fail to boot because of hardware changes. As soon as you an get it to boot, it will probably be back to normal again from then on. Who knows why.

I'll keep thinking about it, but that's the best I can come up with for now. Hopefully it will do the trick. 

Regards, Herman.

---

### Post by vk99 on 2007-02-25
Hi,

Thanks a tonne Herman, it did work, :) well at least partially, now i can boot XP using the floppy...it still doesnt work without the floppy.
Heres what Administration>Disks says about my hard drives on Ubuntu
/dev/hda1 windows NTFS (this is where WinXP is installed)
/dev/hda3 Ext3 (Ubuntu fits in here)
Swap 
/dev/hda5 vfat
/dev/hdb1 vfat( first partition on the 40GB disk i added)
/dev/hdb5 vfat( second partition on the 40GB disk i added)
/dev/hdd1 vfat( the old 2 GD HDD)

is there a way i could re-install GRUB, maybe it will detect WinXP then? its a thought...wot say guys?
thanks again Herman

---

### Post by Herman on 2007-02-25
Well you can always try re-installing grub, it isn't likely to do any harm, and it might help, you never know.                                                        [Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

What I am thinking about is how can we run a few simple tests to try to determine where the problems lays and maybe even pin-point the exact problem so we will know what to fix. How about trying to boot your Windows with another grub like maybe  [Super Grub Disk]("http://supergrub.forjamari.linex.org/"). That will try to boot your Windows by its boot sector the same as your hard disk installed grub does. Therefore if Super Grub Disk can boot your Windows successfully, it will be a good indication that the fault lays in your hard disk installed grub, and we'll go looking for a way to fix that.
On the other hand, if Super Grub Disk fails to chainload your Windows the same as your hard disk installed grub is doing, we will look at what might be wrong with your Windows installation and how we might fix it.

[                              GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") is another one that can chainload Windows if Windows is bootable by normal methods. Perhaps you already have one of those on System Rescue CD and don't realize it? If not they are free and only a small download.

Regards, Herman :)

---

### Post by oilchangeguy on 2007-02-25
i've never run a third hd slaved off the cd drive. i add an ide controller card, set the hd jumper to master

---

### Post by vk99 on 2007-02-26
I did try the Super Grub Disk (on a floppy)... it wasnt able to chainload windows,heres what it said when i selected the Boot Windows option:
Booting 'Boot Windows'
root noverify (hd0,0)
chainloader+1
boot
and then two ASCII characters, the same ALT+212 char and the same boxed smiley that i get on the Grub installed in the Hard Disk. I have not tried the GAG Boot Manager yet.

---

### Post by Onurzaim on 2007-02-26
I can suggest you disabling one of your drives(linux one first) from bios and reboot computer.

If you cant see your windows booting then backup your grub and try doing this for windows xp.

1- Seperate your linux hdd orbackup your linux loading interface in a floppy disk. You can also learn how to restore your grup after installing windows from community help files.

2- Instert you windows xp cd in to drive and boot your comp from it

3- After main drivers loading select rescuse console (F3) or (R). I cant rememeber it well.

4- After that you'll see Dos like screen and pick your windows partition from selection.

5- Now write fixmbr

6- Then fix boot

7- Type reboot.

Now I think you'll be able to boot from only windows Xp. 

in 1st selection I told you you to back up your grub to floppy or cd with booting option or read 

[https://help.ubuntu.com/6.10/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html](https://help.ubuntu.com/6.10/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html)

There are nice tips for getting your linux back on your Os selector screen.

I hope I understood your problem well and it will be solved after this.

---

### Post by vk99 on 2007-02-26
i tried a few things:
1)Ran FIXMBR from my Windows XP Installation CD - i ended up not being able to boot at    all(neither Ubuntu not XP).
2)Booted XP with the startup floppy i created from one of your previous posts - ran sytem restore - no go - still no OS to boot
3)Restored Grub from Super Grub Disk - now i have Ubuntu back up and running.
just playing around here ... i mean nothing ventured nothing gained! Back to square one though. :)

@onurzaim
I have both Ubuntu and Windows XP on the same HDD

---

### Post by Duck2006 on 2007-02-26
In your menu.lst file

root noverify (hd0,0)
chainloader +1
boot

Sould read

rootnoverify (hd0,0)
chainloader +1
boot

or

root (hd0,0)
chainloader +1
boot

---

### Post by vk99 on 2007-02-26
we fixed it! yee haw!!! 
ok heres how it went:
i booted using my WinXP install CD
>choose option to repair
>logged in to WinXP installation
>C:\windows
>typed fixmbr,then fixboot
>rebooted
at this stage WinXP was the only OS i could boot into without using floppies.
then i used Super Grub Disk to Fix Linux(i dont remember the exact name, it was the first option after choosing GNU/Linux--it rewrote MBR with GRUB)
>at this stage i could only boot Linux
>upon booting linux I opened terminal and typed:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
and then made sure the stuff below was on there
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1
---------------------------------------------Reboot and we're back in business!
Thanks a tonne to Herman,Onurzaim,Kateikyoushi,Duck2006.
Hope this will be of use to others :)

---

