---
title: "Ubuntu does not boot"
date: 2011-07-14
forum: Apple Hardware Users
---

### Post by zatix on 2011-07-14
I just reinstalled ubuntu to the new version in my macbook pro, I have rEFIt which properly boots mac osx but for some reason it is not able to boot the new installation of ubuntu.

I made the common installation (ext4 partition mounting / and one for the swap), then I restart I sync the partitions with rEFIt and mac osx boots well but the ubuntu gets stuck and I never get to see the grub.

should I modify something else?

many thanks.

---

### Post by zatix on 2011-07-15
I installed the 64 bits version of ubuntu 11.04, is this ok?

---

### Post by zatix on 2011-07-16
Now I have the followving problem:

When I power on the macbook I hear a beep and I only see a black screen, I have to reboot four times to get to the reflt menu, I guess I broke the MBR, any idea about how to fix it?

this is my disk:

> 

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     61850249  Mac OS X HFS+
 3      340213760    342310911  Linux Swap
 4       61851648    340213759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     61850249  af  Mac OS X HFS+
 3      340213760    342310911  82  Linux swap / Solaris
 4 *     61851648    340213759  83  Linux

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

Partition at LBA 340213760:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 61851648:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active
[/QUOTE]

many thanks

---

### Post by zatix on 2011-07-16
I updated the MBR and syncronized to the gpt but still I have to reboot 4 times to see the reflt menu, the disk looks like:


```
** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     61850249  Mac OS X HFS+
 3      340213760    342310911  Linux Swap
 4       61851648    340213759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1 *            1       409639  ee  EFI Protective
 2         409640     61850249  af  Mac OS X HFS+
 3      340213760    342310911  82  Linux swap / Solaris
 4       61851648    340213759  83  Linux

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

Partition at LBA 340213760:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 61851648:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux


```

---

### Post by srs5694 on 2011-07-16
I vaguely recall hearing about the need to reboot multiple times as you describe being a symptom of firmware that's been damaged; however, my memory of this is rather foggy. You might want to investigate that possibility, though, and if you can find corroboration for this hypothesis, download whatever firmware update is available from Apple and flash it. Don't do this unless you can get corroboration, though; firmware update operations are a bit risky; if something goes wrong, it could completely brick the computer.

---

### Post by zatix on 2011-07-17
I am afraid this is my case as I reinstalled everything and tried so many things and I still have this problem, do you know where can I get this firmwire?

thanks

---

### Post by linuxopjemac on 2011-07-17
What is your exact model ? Link in everymac.com pls.

---

### Post by zatix on 2011-07-22
I fixed the issue by reinstalling again the firmware, I followed the instructions of this link [http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/)

Now I am running both linux and mac osx, thanks all :D

---

