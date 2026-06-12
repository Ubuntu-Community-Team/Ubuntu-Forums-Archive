---
title: "Fresh Jaunty installation: GRUB problem"
date: 2009-04-24
forum: Apple Hardware Users
---

### Post by berlandb on 2009-04-24
Hi,

I'm attempting a fresh installation of Kubuntu 9.04 on a MacBook Pro 4,1. I have been using 8.04 and 8.10 on this machine and didn't encounter any installation problems with those versions.

This installation was the first to ask me where to install GRUB, however (I think), and it's a problem I don't seem to be able to resolve. I found many threads about this, but I was unable to apply the suggestions to my own case so far. So I'm sorry for another GRUB thread, but I do need some special attention. :/

This is the problem: when I start up the computer, refit recognizes 2 linux partitions, although there is only 1 linux installation. the first says "boot from HD", the second says "boot from partition 3". No matter which one I choose, I get to a black screen that says nothing but "GRUB _" and that does not react to any input.

I did not to forget to update the MBR with reFit.

I tried installing an encrypted LVM with a separate /boot partition like I'm used to, but when that failed I also tried a standard guided partition scheme (root and swap).

I am dual booting with OS X, so my disk's layout looks like this:

#1 EFI
#2 OS X HFS+
#3 ubuntu root
#4 swap

or when encrypted
#3 /boot
#4 encryption container

Just to be clear: I am supposed to install GRUB into the bootable partition that contains /boot, right? In both the above cases I would have to type in '/dev/sda3' when asked where to install GRUB. Right?

Thank you so much for your help.

---

### Post by Rog-Mahal on 2009-04-24
*Bump* Have the same issue after following the same instructions. Not sure if it matters, but I manually edited the partition table and also formatted to ext4.

Here's the output of my partition inspection from OS X:
```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     31342631  Mac OS X HFS+
 3       31604351    234440288  Basic Data
 4       31342632     31604350  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     31342631  af  Mac OS X HFS+
 3 *     31604351    234440288  83  Linux
 4       31342632     31604350  82  Linux swap / Solaris

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

Partition at LBA 31604351:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 31342632:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

```

---

### Post by cyberdork33 on 2009-04-24
berlandb, 

You have two linux icons because you have grub installed in two different places. One is likely in the MBR while the other is on a partition. If you can get teh partition inspector report like Rog's we can see exactly where. (/Application/Utilities/Partition Inspector)

Rog, you have grub on partition 3 and in the MBR. I would suggest deleting the Linux partitions (removing GRUB from partition 3) then reinstall and choose to install to the MBR (default location). That would be safer for your other data then trying to remove it from the MBR. (berlandb, I would suggest something similar for you, but you have to find the specific partitions that you are using.)

NOTE: Normally, we suggest installing to the Ubuntu bootable partition, but it is not an issue if you are not also installing Windows on the machine)

---

### Post by berlandb on 2009-04-25
> **cyberdork33 said:**
> berlandb, 

You have two linux icons because you have grub installed in two different places. One is likely in the MBR while the other is on a partition. If you can get teh partition inspector report like Rog's we can see exactly where. (/Application/Utilities/Partition Inspector)

Thank you for your reply. Here is the report
```


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    146948135  Mac OS X HFS+
 3      146948136    147436417  EFI System (FAT)
 4      147436418    390721934  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    146948135  af  Mac OS X HFS+
 3 *    146948136    147436417  83  Linux
 4      147436418    390721934  0b  FAT32 (CHS)

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

Partition at LBA 146948136:
 Boot Code: GRUB
 File System: ext2
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 147436418:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 0b  FAT32 (CHS)

```

> **cyberdork33 said:**
> 
Rog, you have grub on partition 3 and in the MBR. I would suggest deleting the Linux partitions (removing GRUB from partition 3) then reinstall and choose to install to the MBR (default location). That would be safer for your other data then trying to remove it from the MBR. (berlandb, I would suggest something similar for you, but you have to find the specific partitions that you are using.)

In previous Ubuntu installations I believe that have been asked whether I want to install GRUB to the MBR -- yes or no -- and went with the default.

Now I have to type in something specific without any help or info about what would be the default. Could you please tell me how to specify the MBR as the GRUB installation location?

Thank you for your help!

---

### Post by cyberdork33 on 2009-04-25
> **berlandb said:**
>  In previous Ubuntu installations I believe that have been asked whether I want to install GRUB to the MBR -- yes or no -- and went with the default.

Now I have to type in something specific without any help or info about what would be the default. Could you please tell me how to specify the MBR as the GRUB installation location?
That is weird, it must be something that is specific to kubuntu as the Ubuntu installer has a dropdown (and you can't get to that without first clicking the "Advanced" button before the installation actually starts).

You MBR for your primary hard drive should be indicated by (hd0). You do, in fact, have grub installed in both the ubuntu partition and the MBR currently, so to avoid the two icon problem in rEFIt, you should completely delete your current kubuntu partitions (root and swap), then install to the "largest free space". Then install grub to the MBR as discussed. Good Luck!

---

### Post by Rog-Mahal on 2009-04-25
I tried installing using the defaults like cyberdork suggested and now I'm booting fine. One icon per OS and no problems. Should the wiki page be edited so that other people don't run into this problem? Why not just install GRUB to the MBR all the time?

---

### Post by cyberdork33 on 2009-04-25
> **Rog-Mahal said:**
> Should the wiki page be edited so that other people don't run into this problem? 
If you follow the wiki, you should not end up in the situation you were in. If you feel that this is kubunutu specific, then it might be worth noting:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

> **Rog-Mahal said:**
> Why not just install GRUB to the MBR all the time?
This is a complicated question... (well, not really complicated, but has a long explanation).

Most PCs are only capable of starting bootcode in the MBR. This is where the BIOS looks for the code to start the boot process. As a result of this, most Operating Systems want to install their bootcode to the MBR. Ubuntu is friendly in this regard, and, when installing GRUB to the default location (MBR) it displaces any Windows bootcode there, but has the functionality to start the Windows bootloader on the Windows partition itself, and adds an entry to do this into the Grub Menu. Windows, however, is not friendly to other operating systems, and simply overwrites bootcode in the MBR without asking, without allowing for any other configuration. 

Ok, now to the Intel Mac. Intel-based Macs have EFI, and emulates some of the BIOS functions that allow "legacy operating systems" to boot. EFI is capable of booting bootcode on a partition directly instead of only looking in the MBR. Now, you can treat the Mac like a PC and just install GRUB to the MBR overwriting the bootcode for any other operating system, (though it does this gracefully as mentioned above). However, if you do this, you now have to choose Windows (or Linux) in rEFIt, which will both start the code in the MBR (GRUB) then you will have to choose to boot Windows or any other OS bootloader from GRUB (i.e. you have to go through two different menus to get to windows). Since the Mac doesn't have to boot from the MBR (because of its EFI capabilities), it makes more sense to install each operating systems bootcode in it's own location, starting it directly from rEFIt. In the case of windows however, it can ONLY install to the MBR, so we essentially reserve the MBR for it's use.

Basically, if you are not using windows in addition to Linux on your Mac, it doesn't matter where you install GRUB, it won't affect the operation.

Hope this explains things a bit more. It was really a result of many people complaining about having to go through GRUB to get to Windows, whereas possibly getting two Linux icons in rEFIt might not look ideal, it doesn't "break" anything and both icons are still functional.

---

### Post by Rog-Mahal on 2009-04-25
ah, makes a lot of sense :) but from your description it seems odd that when I installed grub to my Linux partition I ended up with two non-functioning icons. Oh well, I have a fully functioning dual boot macbook now!

---

### Post by cyberdork33 on 2009-04-27
> **Rog-Mahal said:**
> ah, makes a lot of sense :) but from your description it seems odd that when I installed grub to my Linux partition I ended up with two non-functioning icons. Oh well, I have a fully functioning dual boot macbook now! both installations were not pointing to the right partition? IDK.

---

### Post by zygut on 2009-05-03
> **cyberdork33 said:**
> If you follow the wiki, you should not end up in the situation you were in. If you feel that this is kubunutu specific, then it might be worth noting:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

The wiki says to do this:
[INDENT]
# Start the Ubuntu Installer from the desktop icon. When prompted, choose to install to the “largest continuous free space”. This will let the installer create a root partition and a swap partition in the free space you made. On the last dialog of the installer, be sure to click the “Advanced” button and choose to install grub to /dev/sda3. [/INDENT]

As you can see, if you follow these directions, you are instructed to install grub in /dev/sda3, not in the MBR!

---

### Post by cyberdork33 on 2009-05-03
> **zygut said:**
> As you can see, if you follow these directions, you are instructed to install grub in /dev/sda3, not in the MBR!
Yes, and you should install to your partition, not the MBR, but if you already did install to the MBR, then that changes things.

---

### Post by vindvaki on 2009-05-13
Hi, I seem to have a very similar problem. What I find strange is that I had already been able to boot into Jaunty a couple of times before GRUB suddenly stopped working. 

Before I shut down my MacBook and went to sleep last night, everything worked. When I woke up and tried to boot Jaunty, GRUB was broken. Luckily, Mac OS X still works.

The last things I recall changing were some linux-backports for better ath9k wireless performance and removing mouseemu to get F11 and F12 back. However, I had already rebooted the machine once after that whithout a problem, before I went to sleep.

Note that I already had a non-working GRUB in the MBR, the one that stopped working was on the Ubuntu partition.

---

