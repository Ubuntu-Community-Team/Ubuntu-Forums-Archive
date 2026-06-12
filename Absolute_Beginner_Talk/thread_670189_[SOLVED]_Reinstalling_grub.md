---
title: "[SOLVED] Reinstalling grub"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2008-01-17
Ok guys i searched thru quite a lot and kinda not finding the right solution to any of my problem.

My hdd's look like this :
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x461e461d

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS**
/dev/sda2            4866       19457   117210240    f  W95 Ext'd (LBA)
/dev/sda5            4866        9730    39078081    b  W95 FAT32
/dev/sda6            9731       14595    39078081    b  W95 FAT32
/dev/sda7           14596       19457    39053983+   b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f9f1f9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         973     7815591    b  W95 FAT32
/dev/sdb2             974        4865    31262490    f  W95 Ext'd (LBA)
/dev/sdb5             974        1937     7743298+   b  W95 FAT32
/dev/sdb6            1938        2902     7751331    b  W95 FAT32
[B]/dev/sdb7            3027        4865    14771736   83  Linux
/dev/sdb8            2903        3026      995998+  82  Linux swap / Solaris[/B]

i reinstalled Windows XP on /dev/sda1 (it was dual boot from the same drive earlier) and as expected cant get to boot into ubuntu. I followed this particular thread to get the grub back...

> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

i followed the steps and got the following result...

> grub> find /boot/grub/stage1
 (hd1,6)

grub> root (<tab> 
 Possible disks are:  hd0 hd1

grub> root (hd1,6)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

but on restart GRUB still does not boot! i guess i am writing the MBR of hd1 but XP is booting from hd0. So somehow i need to write the same into hd0. but the setup has been always like this. I mean i just rewrote XP on the same drive as it was earlier. please help!

---

### Post by Sef on 2008-01-17
I would download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") to reinstall GRUB.

---

### Post by kpkeerthi on 2008-01-17
The steps you followed to reinstall grub is right. But your linux partition /dev/sdb7 is not bootable. No star * under boot column for dev/sda7. /dev/sda1 and /dev/sdb1 has *. Did you see it?

---

### Post by koleoptero on 2008-01-17
Do that again, but change setup to: setup(hd0)

It should install on the first drives mbr. If that doesn't work and you have multiple drives then try hd1 hd2 etc.

---

### Post by Hightide on 2008-01-17
I had the same problem,  downloaded supergrub, reinstalled and  all is fine

:)

---

### Post by lswest on 2008-01-17
also you could configure the XP bootloader to boot to grub using EasyBCD if all else fails

---

### Post by badguyanil on 2008-01-17
Thanks all for the quick response but....

> **Sef said:**
> I would download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") to reinstall GRUB.
Thank you for the suggestion will try this one as the last option!

> **kpkeerthi said:**
> The steps you followed to reinstall grub is right. But your linux partition /dev/sdb7 is not bootable. No star * under boot column for dev/sda7. /dev/sda1 and /dev/sdb1 has *. Did you see it?
Yeh you are right i thought of the same initially! but remember Ubuntu has alwyas been on that drive. I just reinstalled XP on sda1 and that i think did not change the second hdd at all! So althoiugh you are right would wait for some more insight!

> **koleoptero said:**
> Do that again, but change setup to: setup(hd0)

It should install on the first drives mbr. If that doesn't work and you have multiple drives then try hd1 hd2 etc.
well tried with hd0. It gives an error saying the destination drive cannot be mounted. will try hd1, hd2 etc and let you know. But that is just trial and error! there must be some more logical expanation to what i try. Dont you think :D

> **Hightide said:**
> I had the same problem,  downloaded supergrub, reinstalled and  all is fine
:)
Oh thanks for that! so one thing for sure the problem is solvable atleast by some 3rd party tool :D. Will try this as the last option buddy!

> **lswest said:**
> also you could configure the XP bootloader to boot to grub using EasyBCD if all else fails
Hmm this is also an option! but can we not get the setup as it was earlier... would like to try a bit of experimentation before i try anything from windows...

---

### Post by itix on 2008-01-17
Super Grub Disc :D
It worked for me many times while I still ran windows :)

---

### Post by cecilpierce on 2008-01-17
Computer boots from first HD (hd0), unless you changed it in the
bios. Grub setup should have been setup (hd0)

---

### Post by badguyanil on 2008-01-17
> **cecilpierce said:**
> Computer boots from first HD (hd0), unless you changed it in the
bios. Grub setup should have been setup (hd0)

So what do you suggest i do? and i havent changed anything in bios. It is just as it was after and before reinstallation of windows. Any suggestions........

---

### Post by badguyanil on 2008-01-17
> **itix said:**
> Super Grub Disc :D
It worked for me many times while I still ran windows :)

Guys seem addictied to Super Gub... never used it but definitly looks a great tool! Quite a few have suggested the same. Will try as my lat option. Thanks for the advice :D

---

### Post by cecilpierce on 2008-01-17
Run grub again and this time put in ....setup (hd0)  where you said 
setup (hd1)
If you have to use the install CD and get into a terminal window as root
(sudo grub)
find /boot/grub/stage1
root (hd1,6)
setup (hd0)
quit

---

### Post by bumanie on 2008-01-17
I think you can put the following into terminal and then manually flag the partition you want bootable (in your case sdb7)
sudo cfdisk
I think this overwrites the file system table and then you can try to reinstall grub if this doesn't fix the problem straight away. If the only problem is to flag sdb7, cfdisk should work. If it doesn't work you can re-enter cfdisk and reverse what you have done.

---

### Post by badguyanil on 2008-01-17
> **cecilpierce said:**
> Run grub again and this time put in ....setup (hd0)  where you said 
setup (hd1)
If you have to use the install CD and get into a terminal window as root
(sudo grub)
find /boot/grub/stage1
root (hd1,6)
setup (hd0)
quit

Yeh! this did the trick! grub loading just fine :D

> **bumanie said:**
> I think you can put the following into terminal and then manually flag the partition you want bootable (in your case sdb7)
sudo cfdisk
I think this overwrites the file system table and then you can try to reinstall grub if this doesn't fix the problem straight away. If the only problem is to flag sdb7, cfdisk should work. If it doesn't work you can re-enter cfdisk and reverse what you have done.

Did not need this but thanks a ton for the help!

All the SUPER GRUB fans! well this was very simple! why go the super grub way then  ;)

---

