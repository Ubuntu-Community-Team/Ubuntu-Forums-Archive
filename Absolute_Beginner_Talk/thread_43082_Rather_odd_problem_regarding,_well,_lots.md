---
title: "Rather odd problem regarding, well, lots"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by topcat on 2005-06-20
Hi, I have a very long and seemingly hard-to-fix problem. I've installed Ubuntu, using expert mode primarily because I wanted to keep my existing files/ data on Windows. The installation proceeded with some hitches-- the installer told me several times that it was unable to load (or something along those lines) the files/ whatever ide-mod, ide-probe-mod, ide-detect and ide-floppy. However, the installer said that I should proably proceed with installation as the files may become available later. The real problem came when I came to install a bootloader. I chose to install the GRUB loader in the MBR, which seemed to install fine, but when it came to the reboot I was presented with an Error 17. Fine, I thought, I'd just put the LiveCD in and search for a resolution. No such luck. On the advice of a friend, who used Slackware before migrating to FreeBSD, I reinstalled Ubuntu, overwriting the partitions. Hoping to avoid the problems with GRUB, I installed LILO instead. I chose to install it in out of the MBR. This time on reboot I got the error message along the lines of "NO PARTITION MOUNTED PLEASE INSERT SYSTEM DISK". Lacking a Windows system disk, and seemingly without a Ubuntu system disk (the installer, I know, but utter beginner etc), I just inserted the LiveCD again. Following the same friend's advice, I did a few commands, found partitions etc but after what was probably a nasty command, which, unfortunately, I can't remember, the system seemed to either not recognise or merge the partitions into a single hda. As you can understand, this didn't make matters much better. My friend did point out several tools, including gpart, but as I am running off a livecd version installing or running them isn't totally easy or, perhaps, possible. I have toyed with using a Windows boot CD; however, I don't have one and obtaining one may be somewhat difficult- unless they sell them at computing shops.
Regarding the hda mashup, it will not recognise any partition, if any still exists. A fdisk -l returned
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
```
to me earlier, but now it will not execute an fdisk at all. I am wondering, actually, whether Windows still exists on my computer (although I have been reassured that it does). The boot loader still returns an error with mounted partitions, telling me to insert a system disk. Meanwhile, loading Synaptic, it says that I haven't installed Grub or Lilo, which is worrying, to say the least. I am assuming that it is possible to fix this problem; I am hoping that the way to fix it doesn't require me to lose all my data or pay someone to do it, and that it can be done using a LiveCD. Bear in mind that I haven't got a Windows boot disk, or at least one I can find, and my knowledge of Unix/ Linux commands is rather limited.
(Sorry about the horrible formatting here. Similarly sorry if it's in the wrong forum; I just assumed this would be the place to ask as I am an absolute beginner.)

edit: You might want my system specs:
AMD Athlon 2700+ (2.16 GhZ)
512 MB RAM
NVIDEA GeForce FX 5200 Graphics Card
A Sound Card
One 120 GB Hard Drive

---

### Post by chaumurky on 2005-06-20
[QUOTE=topcat]Hi, I have a very long and seemingly hard-to-fix problem. I've installed Ubuntu, using expert mode primarily because I wanted to keep my existing files/ data on Windows. The installation proceeded with some hitches-- the installer told me several times that it was unable to load (or something along those lines) the files/ whatever ide-mod, ide-probe-mod, ide-detect and ide-floppy. However, the installer said that I should proably proceed with installation as the files may become available later. The real problem came when I came to install a bootloader. I chose to install the GRUB loader in the MBR, which seemed to install fine, but when it came to the reboot I was presented with an Error 17. Fine, I thought, I'd just put the LiveCD in and search for a resolution. No such luck. On the advice of a friend, who used Slackware before migrating to FreeBSD, I reinstalled Ubuntu, overwriting the partitions. Hoping to avoid the problems with GRUB, I installed LILO instead. I chose to install it in out of the MBR. This time on reboot I got the error message along the lines of "NO PARTITION MOUNTED PLEASE INSERT SYSTEM DISK". Lacking a Windows system disk, and seemingly without a Ubuntu system disk (the installer, I know, but utter beginner etc), I just inserted the LiveCD again. Following the same friend's advice, I did a few commands, found partitions etc but after what was probably a nasty command, which, unfortunately, I can't remember, the system seemed to either not recognise or merge the partitions into a single hda. As you can understand, this didn't make matters much better. My friend did point out several tools, including gpart, but as I am running off a livecd version installing or running them isn't totally easy or, perhaps, possible. I have toyed with using a Windows boot CD; however, I don't have one and obtaining one may be somewhat difficult- unless they sell them at computing shops.
Regarding the hda mashup, it will not recognise any partition, if any still exists. A fdisk -l returned
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
```
to me earlier, but now it will not execute an fdisk at all. I am wondering, actually, whether Windows still exists on my computer (although I have been reassured that it does). The boot loader still returns an error with mounted partitions, telling me to insert a system disk. Meanwhile, loading Synaptic, it says that I haven't installed Grub or Lilo, which is worrying, to say the least. I am assuming that it is possible to fix this problem; I am hoping that the way to fix it doesn't require me to lose all my data or pay someone to do it, and that it can be done using a LiveCD. Bear in mind that I haven't got a Windows boot disk, or at least one I can find, and my knowledge of Unix/ Linux commands is rather limited.
(Sorry about the horrible formatting here. Similarly sorry if it's in the wrong forum; I just assumed this would be the place to ask as I am an absolute beginner.)

edit: You might want my system specs:
AMD Athlon 2700+ (2.16 GhZ)
512 MB RAM
NVIDEA GeForce FX 5200 Graphics Card
A Sound Card
One 120 GB Hard Drive[/QUOTE]
 IMO you really need to get this drive on another computer already running Windows. Get a hold of a file recovery program like R-Studio (which can read damaged partitions) and pull the data off the drive before you go any further. My $0.02...

---

### Post by topcat on 2005-06-21
[QUOTE=chaumurky]IMO you really need to get this drive on another computer already running Windows. Get a hold of a file recovery program like R-Studio (which can read damaged partitions) and pull the data off the drive before you go any further. My $0.02...[/QUOTE]
 That'd be helpful, yeah, but the onbly other computer running Windows in the house is a P166 on Windows 95. =//

---

### Post by topcat on 2005-06-21
On the advice of another forum, I did a cfdisk, and it returned this:   
```
                           Disk Drive: /dev/hda
                       Size: 120034123776 bytes, 120.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 14593

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------                      
                                    Pri/Log   Free Space                      120031.52
```
According to someone I know, this means my partition table is broken/ corrupted. Is there any fairly simplish way to fix this with the packages available by default on the LCD or will I need to install something to disk?

---

