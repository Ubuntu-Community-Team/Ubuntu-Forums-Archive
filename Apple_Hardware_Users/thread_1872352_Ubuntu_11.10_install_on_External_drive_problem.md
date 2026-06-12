---
title: "Ubuntu 11.10 install on External drive problem"
date: 2011-10-30
forum: Apple Hardware Users
---

### Post by chick_turk on 2011-10-30
Hello,

So my Mac is dualbooting OSX and Windows 7 with BootCamp, the problem I'm having relates to booting Ubuntu from an external drive. I installed Ubuntu to my external drive, and all went well (installed boot loader to right place as well), but when I then tried to boot, my mac just went straight to my BootCamp partition even though I selected to boot from the external. I'm using rEFIt btw. My other problem lies in the firewire functionality of my drive (seagate with interchangeable usb 3.0 and firewire). For some reason, the drive is not detected by rEFIt when using the firewire attachment, so I have to rely on the usb attachment instead.

PS. Could this be because I installed Ubuntu to the external through a non-Apple computer?

Edit: This drive is partitioned, with one partition being for gaming, the other free space for installing Ubuntu, or any other Linux distro. That can work, right?

---

### Post by pindar on 2011-10-30
Booting Mac hardware from an external USB is possible (I have it working here), but less straightforward than you may wish. AFAIK, the only way to achieve this is:
[LIST=1]
[*]The drive needs to have a GUID partition table. And it needs a small EFI boot partition as the first partition. If you partition your drive with the OS X diskutility, it will automatically add this partition (which is hidden in OS X), so this may be the easiest way.
[*]You need to produce a grub-efi boot image and move it and several other files into this partition. This is best done from a live cd/usb. When refit detects this file inside an EFI partition, it will offer to boot from the disk.
[*]And you will probably need to write your own grub.cfg; if memory serves right, ubuntu will not create a workable config file for you.
[/LIST]
And finally: which imac model do you have? I haven't had any luck booting ubuntu on a very recent imac; the graphic card wouldn't work. 

Good luck

pindar

---

### Post by chick_turk on 2011-10-30
> **pindar said:**
> Booting Mac hardware from an external USB is possible (I have it working here), but less straightforward than you may wish. AFAIK, the only way to achieve this is:
[LIST=1]
[*]The drive needs to have a GUID partition table. And it needs a small EFI boot partition as the first partition. If you partition your drive with the OS X diskutility, it will automatically add this partition (which is hidden in OS X), so this may be the easiest way.
[*]You need to produce a grub-efi boot image and move it and several other files into this partition. This is best done from a live cd/usb. When refit detects this file inside an EFI partition, it will offer to boot from the disk.
[*]And you will probably need to write your own grub.cfg; if memory serves right, ubuntu will not create a workable config file for you.
[/LIST]
And finally: which imac model do you have? I haven't had any luck booting ubuntu on a very recent imac; the graphic card wouldn't work. 

Good luck

pindar

It's a late 2009 21.5". Live CD works perfectly, and installed fine through my Mac. I mean, grub installed fine. If it's GUID, will I still be able to keep that data partition NTFS? I mean, I formatted the partition and everything when installing. So, why does the livecd boot fine, but not the external drive? It doesn't make sense to me. Also, I'm pretty sure by trying to load the drive at boot, an efi partition is made on the disk. 

PS. The firewire part seems to work fine now. Must have been a one-time thing. I also have another external drive hooked up for time machine. Could that also be a problem? Also, rEFIt offers to either boot from a legacy OS form the drive or Linux. Would choosing one over the other make a difference?

Edit: Turns out that rEFIt does that with any external drive. So I guess it really wasn't detecting. Does disk utility let you format a partition as NTFS? Because I run games off of the drive, so if it becomes fat, then there will be no way to copy games to it (as they are all larger than 4.8GB)

---

### Post by pindar on 2011-11-01
Excuse me for being blunt, but you're asking a lot of questions that you can answer yourself: open the drive in gparted from within the live CD, and you'll see if there is an EFI partition and what kind of partition map you have. Open diskutility, and you'll see if it can partition ntfs (I'm not sure, but I don't think so). The fact that your imac can boot from the live CD is completely irrelevant here. If you decide to repartition with GUID, you can't keep anything, all your partitions and the data on them will be gone. And for booting, I would switch off/disconnect any other usb disks - when you'll boot, you'll need to give a "root" parameter to the kernel, and I've seen that with two external drives connected, it's sometimes a bit unpredictable which one will be detected as /dev/sdb and which one as /dev/sdc. So that's another layer of complication that you don't need now. 

Good luck 

pindar

---

### Post by chick_turk on 2011-11-02
> **pindar said:**
> Excuse me for being blunt, but you're asking a lot of questions that you can answer yourself: open the drive in gparted from within the live CD, and you'll see if there is an EFI partition and what kind of partition map you have. Open diskutility, and you'll see if it can partition ntfs (I'm not sure, but I don't think so). The fact that your imac can boot from the live CD is completely irrelevant here. If you decide to repartition with GUID, you can't keep anything, all your partitions and the data on them will be gone. And for booting, I would switch off/disconnect any other usb disks - when you'll boot, you'll need to give a "root" parameter to the kernel, and I've seen that with two external drives connected, it's sometimes a bit unpredictable which one will be detected as /dev/sdb and which one as /dev/sdc. So that's another layer of complication that you don't need now. 

Good luck 

pindar

No, that's quite alright. No need to excuse yourself. So, I backed up the data,  changed it to GUID, formatted it to NTFS in Windows, then copied everything back. Now everything is good and the games are running fine off of the drive. I'll try again sooner or later. I see a 200mb GPT Protective Partition. Would that be the EFI partition you mentioned? Also, it tends to either be SDD or SDC depending on the plugged in devices. The drive is easy to find, as it's the only Seagate connected to my system.

PS. I asked about NTFS *because* Disk Utility gave no option for it. Also, what do you mean by root parameters? Every install I put GRUB on SDC or SDD (if that's what you're talking anout), as in, my external, then install Ubuntu to the free space partition as Ext4 with \ as mount point, leaving out Swap since I have 6gb of memory (plus when I tried to make another partition, it didn't really work).

---

### Post by pindar on 2011-11-04
> **chick_turk said:**
> No, that's quite alright. No need to excuse yourself. So, I backed up the data,  changed it to GUID, formatted it to NTFS in Windows, then copied everything back. Now everything is good and the games are running fine off of the drive. I'll try again sooner or later. I see a 200mb GPT Protective Partition. Would that be the EFI partition you mentioned? Also, it tends to either be SDD or SDC depending on the plugged in devices. The drive is easy to find, as it's the only Seagate connected to my system.

PS. I asked about NTFS *because* Disk Utility gave no option for it. Also, what do you mean by root parameters? Every install I put GRUB on SDC or SDD (if that's what you're talking anout), as in, my external, then install Ubuntu to the free space partition as Ext4 with \ as mount point, leaving out Swap since I have 6gb of memory (plus when I tried to make another partition, it didn't really work).
Good, so you're making progress. Yes, the GPT protected partition is exactly the partition that I mentioned. What you'll need to do with this partition: 

[LIST=1]
[*]Create a directory structure EFI/boot (caps may be significant, so better play ot safe).
[*]Into the EFI/boot directory, copy the grub.efi binary you make from with grub-efi. There is enough information on the forum for that; if you can't find it, report back and I'll see if I can find a link for you.
[*]You will eventually write a grub.cfg file and copy it to the same directory; for the first boot, I would try to boot manually.
[/LIST]

In a nutshell, the commands for a manual boot would be: when grub screen comes up, press "c" and you'll be in a grub shell. Then:
```

set prefix=/efi/boot
fakebios
set root=(hd0,gpt2)
linux=/boot/vmlinuz-3.0.0-12-generic root=/dev/sdb2 noefi
initrd initrd.img-3.0.0-12-generic
boot

```
So that's where the "root" parameter comes into play. 

Good luck

pindar

---

