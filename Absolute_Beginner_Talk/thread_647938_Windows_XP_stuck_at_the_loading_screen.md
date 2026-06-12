---
title: "Windows XP stuck at the loading screen"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by coolboy49932 on 2007-12-22
Hello Everyone, I have a problem because my Windows XP wont load anymore. It used to load, but now it sits on the screen with the bar rolling across the screen. I am a newbie that just started to use linux yesterday and I installed it on my second Harddrive and it seems like not even ubuntus recognizing it. I'll post my menu.lst if I have to. So when I deleted the partition ubuntu was installed in I had a GRUB error 22. So either way I lose. I re-installed Linux and I wanted to get rid of this problem. Feel free to pm me. Thank You.

---

### Post by seshomaru samma on 2007-12-23
coolboyy
i`m sorry but I can`t really understand what is your situation.
Can you post the output for
```
sudo fdisk -l
```
(run this command in a terminal in linux)
does Linux boot?
does Windows start to boot?

---

### Post by LaRoza on 2007-12-23
If you want to get rid of Ubuntu (for now), you can restore the Windows bootloader with the Super Grub Disk. You won't be able to boot Ubuntu if you do this.

See the link in my sig for the SGD.

---

### Post by coolboy49932 on 2007-12-23
I'm sorry for not making this clear, but Windows XP freezes at the loading screen (the one with the bars running across the screen)  everytime I try to load the OS with GRUB. So after I Deleted the Partition with ubuntu installed in it. Then I get this GRUB error 22, then I thought of installing Ubuntu again. Now I want to get the Windows XP fixed without it getting stuck at the loading screen. If that does not work out, I need to uninstall ubuntu without getting a GRUB error 22. Please help me. Thank You!

---

### Post by coolboy49932 on 2007-12-23
Yes Linux Boots but Windows gets stuck at the loading screen at the beginning and never get into the user login page. Heres the sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05ba3718

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1276       19457   146046915    7  HPFS/NTFS
/dev/sda2               1         956     7679038+  83  Linux
/dev/sda3             957        1122     1333395    b  W95 FAT32
/dev/sda4            1123        1275     1228972+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
240 heads, 63 sectors/track, 7943 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xfcb1ec06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7942    60041488+   7  HPFS/NTFS

```

---

### Post by Pumalite on 2007-12-23
Boot from your XP Installation disk>Recovery>FIXMBR>FIXBOOT
If you don't have a CD, do what they have suggested, use Super Grub to fix your Windows MBR.

---

### Post by seshomaru samma on 2007-12-23
What pumalite suggested will get rid of Grub and will leave you with a pure Windows install however if the problem still occurs ,I'm afraid that you will have to fix your Winodws installation.
I think there is a recovery option in the Windows CD. It reinstall the OS without touching your files and settings. you need to choose this option "To setup Windows XP now, press ENTER" (not the R option) then the CD will look for exisiting Windows installations ,It will find your install and you will have the option to fix it.
However . I would look for a Windows forum for better instructions. If you have important docs on Windows - save them first with the Ubuntu Live CD.

---

### Post by Tyke91 on 2007-12-23
I've had this problem also. the way I fixed it was to boot from a windows CD, go to the window command line, and type

```
CHKDSK
```

this fixed my windows installation (that I haven't used for 3 weeks now... must buy more videogames)

---

### Post by Bartender on 2007-12-23
It's unlikely that you've damaged your Windows operating system and personal data.  The only part of the Windows installation that has been changed is the Windows Master Boot Record.  When you dual-boot in the typical fashion the GRUB bootloader tweaks the MBR so that you get the choice of booting Windows or Linux.  
When you uninstall Linux, the GRUB bootloader gets mixed up and you don't get the choice of systems to boot.  Re-installing Linux may have just made it worse.

As others have suggested, fix the MBR with a real true Windows CD (not a "recovery CD") or use another tool like Super GRUB CD.  There are many guides on the net for fixing MBR.

---

### Post by Wiebelhaus on 2007-12-23
that's just a hidden feature , I say good... let the dead dog lie.

---

