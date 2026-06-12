---
title: "grub hangs after memory upgrade (4gb, ram, stage2)"
date: 2009-06-29
forum: Apple Hardware Users
---

### Post by PauloM on 2009-06-29
Hello friends,

after finishing the install process of osx and linux on 
my Macbook Early09 MB881LL/A, i was quite happy
and everything was working as expected. Booting from 
efis boot selector or with refit was working (grub comes 
up etc.). 

```

/dev/disk0 
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *465.8 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Sys                     300.9 Gi   disk0s2
   3:       Microsoft Basic Data                         160.0 Gi   disk0s3
   4:                 Linux Swap                         4.6 Gi     disk0s4

```

Time passes and after trying booting linux again, grub was
no more able to come up and didn't show the kernel menu.
Via Rescue cd and disabling the splash background, i saw
that after loading stage2 the screen clears and just an 
underscore "_" stands in the upper left corner. 

I tried everything (several times):

 1. reinstalling grub onto sda3
 2. changing boot loader to lilo (hangs also etc.)
 3. revert to grub

today i come up with an idea:
Between working and non working linux, i had done an 
memory upgrade from 2gb to 4gb. Fortunately i keep the 
old Dimms an reinstalled them (2x1gb) ...  and ... the linux
system is booting again (puuuh - what a time killer).

Okay - where lies the reason for this behavior ?

For the first step (making two partitions) i used bootcamp 
(2gb ram where installed).
Is boot camp writing some memory information to efi 
to be able to emulate the bios environment?  This would 
say: "Do everything with 4gb installed" :-( 

or

is grub (0.97) unable ... (Some confirmation needed: Has someone
a working system (grub0.97+4gb+legacy bios boot method)?

So far and looking forward.

Regards

Paulo

PS:
```


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    631390247  Mac OS X HFS+
 3      631654400    967196671  Basic Data
 4      967198720    976773119  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    631390247  af  Mac OS X HFS+
 3 *    631654400    967196671  83  Linux
 4      967198720    976773119  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 631654400:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 967198720:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris




```

---

### Post by Richardcavell on 2009-06-29
Paulo,

I'm not sure what the problem is with your computer. However, you asked for confirmation that GRUB can cope with 4 Gigs of RAM. I have a second-generation plain MacBook. It had 1 Gig RAM and ran OS X and Ubuntu fine. I upgraded it to 4 Gigs. (Early MacBooks have a hardware limitation that means that they can only address a little over 3 Gigs of it). Ubuntu and OS X just recognised the memory and didn't skip a beat. So I can confirm that it should work. I'm booting 4 Gigs with GRUB 0.97 and legacy boot method. No problemmo.

Not to state the obvious, but have you done a memtest?  Do it from the Ubuntu Live CD. Do you have matched pairs?

Richard

---

### Post by PauloM on 2009-06-29
Hi Richard,  thanks for the confirmation! 

The Macbook MB881LL is quit new and supports up to 4Gb RAM. Also OSX had no problem
(4Gb recognized) with these two Kingston DIMMs (KTA-MB667K2/4G 4GB Kit).
These hints shouldn't be the reason.

Well - after a lot of time of investigation, i can at least empirically say "it has to do with
the memory". Therefore i suppose that efi setup up the legacy mode wrong and inevitably
grub fails. These could also completely wrong ...

Bests

Paulo

---

### Post by Richardcavell on 2009-06-29
Paulo,

Give the memory a good test with memtest86. Also, try uninstalling one of the RAM cards and putting in one of your old ones, to force your motherboard into asymmetric mode, and try it again with memtest86 and then trying to boot Linux. I really don't think GRUB should be having problems because you have 4 Gigs. By the way, my Partition Inspector output is identical to your own (except the start and end blocks), and it works fine.

Richard

---

### Post by PauloM on 2009-06-30
**Configurations**

4Gb (2  x2Gb Dimms) - grub doesn't come up, after loading stage2 the screen clears and just an 
                      underscore "_" stands in the upper left corner (no splash image configured).
3Gb (2Gb+1Gb Dimms) - grub shows menu
2Gb (2  x1Gb Dimms) - grub shows menu 


**memtest86**
memtest86 from various Distributions CD/DVDs doesn't start.
Also here: The screen clears and just an underscore "_" stands in the upper left corner.

Only the memtest86-iso-image (2.11+) from memtest86's homepage is usable.
It starts but no keyboard interaction possible.

**Hardware**
Macbook: MB881LL (Early 2009)
Boot-ROM-Version:    MB52.0088.B02 
SMC-Version (EFI):    1.38f5
NVIDIA GeForce 9400M: **VRAM 256 MB from system memory!**

**Negative confirmation about bootcamp internals**
I used an second harddrive to add partitions via bootcamp (4GB installed).
My assumption above (first post) about bootcamp internals (writing 
informations into EFI) can't be confirmed - it make no difference. 






Sure that grub (bioses) generally can handle 4GB+ - but sharing VRAM and 
setting legacy bios mode with 4Gb seems to me to be the problem that sits 
one step before grub (at least on this specific hardware configuration).

Waiting for a firmware update ... :-)

Paulo

---

### Post by Richardcavell on 2009-06-30
Have you tested each of your new 2 Gig sticks with one of the old sticks in an asymmetric configuration? Make sure you exhaustively check each of the sticks with memtest86 before you declare that they're working properly.

I haven't seen other reports of incompatibilities between the NVidia 9400M and Ubuntu, or any other type of Linux.

Richard

---

