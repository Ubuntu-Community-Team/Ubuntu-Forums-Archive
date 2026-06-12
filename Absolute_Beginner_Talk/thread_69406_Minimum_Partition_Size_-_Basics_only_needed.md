---
title: "Minimum Partition Size - Basics only needed"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by Zxian on 2005-09-26
**[center]===== Question 1 =====[/center]**
I'm thinking about setting up an Ubuntu dual-boot on my laptop since I often need to run applications through an X11 server for my computer science courses (all the servers are running Unix).

The size of Ubuntu is appealing (1 CD vs 3-5 for other distros) since it means that I'll get the basics and only what I need. Speaking of that... I'll need:

[LIST]
[*]Web browser (Opera probably)
[*]Terminal with SSH
[*]Emacs
[*]gcc
[*]PDF Viewer
[*]Wireless capabilties (everything at my university is wireless)
[*]Ability to connect to a VPN server
[/LIST]
I'm wondering how much space I should reserve for Ubuntu and the swap space. I've got it running on a 5GB VMware hard drive and it's using about 1.5GB (I haven't got any drivers or emacs installed, just the base install) and the swap drive is ~200MB. Can I get away with 2 or 3GB? I've got an 80GB drive that's pretty full as it is, so if I can get away with using as little space as possible, that'd be great. I probably won't be saving files in my Ubuntu, and if I do, they'll be small text files...



**[center]===== Question 2 =====[/center]**
Also, I've found the guide on how to install Ubuntu without modifying the Windows MBR (which I'd like to do), but my laptop doesn't have a floppy drive, and all my other partitions are NTFS (I'd prefer not to have to convert them to FAT32). Does anyone have any suggestions on how to do this? Would it be possible to:

[LIST]
[*]Install Ubuntu and install GRUB to MBR
[*]Somehow copy GRUB files from MBR to Windows boot partition
[*]FIXMBR (from Windows recovery disk/console)
[*]Add Ubuntu boot information to boot.ini file
[/LIST]

???

Or can the GRUB installer write the necessary files to an NTFS partition (I don't think this is possible)? And then from there boot to Windows RC and do the MBR switch from there?

---

### Post by xequence on 2005-09-26
Do you mean, if you have windows on a NTFS partition, can ubuntu write to the MBR? It did for me.

And the minimum space for an ubuntu install is 300 MB, if you just do the base system. (Type server when you boot up the install CD). This is just the VERY base, nothing like gnome or any applications.

---

### Post by Zxian on 2005-09-26
I'd like to have a GDE such as gnome. I'm not that hardcore... :P

My second question was whether or not Grub could write to an NTFS partition, leaving the Windows MBR intact.

---

### Post by matthewv on 2005-09-26
[QUOTE=Zxian]**[center]===== Question 2 =====[/center]**
Also, I've found the guide on how to install Ubuntu without modifying the Windows MBR (which I'd like to do), but my laptop doesn't have a floppy drive, and all my other partitions are NTFS (I'd prefer not to have to convert them to FAT32). Does anyone have any suggestions on how to do this? Would it be possible to:

[LIST]
[*]Install Ubuntu and install GRUB to MBR
[*]Somehow copy GRUB files from MBR to Windows boot partition
[*]FIXMBR (from Windows recovery disk/console)
[*]Add Ubuntu boot information to boot.ini file
[/LIST]

???

Or can the GRUB installer write the necessary files to an NTFS partition (I don't think this is possible)? And then from there boot to Windows RC and do the MBR switch from there?[/QUOTE]

Why don't you just install grub to your ubuntu root partition and then modify your boot.ini?

---

### Post by az on 2005-09-26
The MBR is on the MBR.  It is not a part of the disk with a filesystem.  It is not vfat or ext3 or NTFS.  But if you want to keep it intact, just do not install grub there, as suggested.

As far as disk space.  You need about 2.1 Gigs, when you take into consideration the swap space and filesystem data.  Once that is created, Ubuntu takes up about 1.8 gigs of Hdd space.  So, go for 2.5 to 3 Gigs and you will be happy.

---

### Post by Zxian on 2005-09-27
Thanks for the quick replies!

So if I were to install GRUB to the Ubuntu partion and then modify the boot.ini file, everything would work?

And I guess 3 GB it is! Thanks azz.

---

### Post by Zxian on 2005-09-29
@matthewv = How would I modify the boot.ini file? 

I've been trying to get this to work in VMware without any luck.I've got the VM set up with two hard drives right now. What I did:
-Install XP on the one hard drive. Leave enough space for a small FAT/FAT32 partition (10MB or whatever)
-Install recovery console (to fix the MBR later)
-Install Ubuntu on the second hard drive.
-From Ubuntu installer, install GRUB to MBR. **
-Computer reboots, Ubuntu continues to install
-Boot into Ubuntu
-Install GRUB to Ubuntu hard drive (/dev/hdb1 in this case)
-Mount FAT partition
-Copy boot sector as in all the guides (dd if=/dev/hdb1 of=bootsect.lnx bs=512 count=1) and copy that to the FAT partition
-Boot into Windows. Copy bootsect.lnx to C:\ and add C:\bootsect.lnx="Ubuntu Linux" to boot.ini file.

So... at this point, we have GRUB on the MBR, the windows bootloader on the first hard drive, and GRUB on the second hard drive. The bootsector that we pulled off the second hard drive should refer to the Ubuntu partition, no? 

By that reasoning, I should be able to boot the computer, select Windows (from GRUB), and then select Ubuntu (from the Windows bootloader). I know it's a really odd setup, but that's the only way that I could see to get it. I tried using Knoppix to copy the boot sector from /dev/hdb1, but for some reason, it doesn't detect a boot sector to copy...

If that works, I should be able to replace GRUB with the Windows boot loader on the MBR.

Or is there something in my method that's completely off?

---

### Post by matthewv on 2005-09-29
I'm not sure exactly what you're asking. What's wrong with just installing grub to the MBR of you're VM and leaving it at that?? or have I missed something?

When I said install grub to ubuntu root partition I meant just install grub on ubuntu partition (/dev/hdb1) and then adding a line like :

multi(0)disk(0)rdisk(0)partition(1)="Ubuntu"

to you're boot.ini

I've never tried it, so I don't know whether that works. The windows bootloader (ntldr) should be able to boot to your ubuntu partition, but the wording about ntldr on the ms knowledge base suggests its designed for ms oses.

EDIT:
Looking at your question 2 from your first post, I've also never had FIXMBR working. I've only ever tried to use it when i've wrecked the MBR but it never helped. Just a side note

---

