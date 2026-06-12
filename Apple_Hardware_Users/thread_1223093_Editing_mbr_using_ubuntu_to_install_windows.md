---
title: "Editing mbr using ubuntu to install windows?"
date: 2009-07-25
forum: Apple Hardware Users
---

### Post by g-man060692 on 2009-07-25
Hi I have a macbook pro that I have been happily dual booting Mac and Ubunutu on. I recently upgraded the hard drive copying the partitions from may old hard drive to the new one using a ubuntu live cd in my desktop. I created an ntfs partition to install windows xp to play some games. The only problem is I have 5 partitions(the efi, Mac, Ubuntu, Swap, and NTFS) so xp can't recognize the ntfs partition due to the 4 partition limit of mbr. The mbr is synced with the gpt using refit.

So does anyone know of a tool for ubuntu or a live boot cd that can edit the just the mbr and not the gpt. So i can make the mac and linux partitions invisible to xp install cd?

---

### Post by pxwpxw on 2009-07-26
> **g-man060692 said:**
> Hi I have a macbook pro that I have been happily dual booting Mac and Ubunutu on. I recently upgraded the hard drive copying the partitions from may old hard drive to the new one using a ubuntu live cd in my desktop. I created an ntfs partition to install windows xp to play some games. The only problem is I have 5 partitions(the efi, Mac, Ubuntu, Swap, and NTFS) so xp can't recognize the ntfs partition due to the 4 partition limit of mbr. The mbr is synced with the gpt using refit.

So does anyone know of a tool for ubuntu or a live boot cd that can edit the just the mbr and not the gpt. So i can make the mac and linux partitions invisible to xp install cd?

It is possible (but dangerous) to edit the MBR partition table manually to show any 4 of the GPT partitions.

As suggested by **billbear** in 
Re: How to bypass the 4-partitions limit? post #17
[http://ubuntuforums.org/showthread.php?t=782803&page=2](http://ubuntuforums.org/showthread.php?t=782803&page=2)

> 
I just type sudo fdisk -e /dev/rdisk0

then edit 2
Do you wish to edit in CHS mode? [no]
Partition offset: see refit partition inspector report
Partition size: calculated from refit partition inspector report

then edit 3, edit 4

Unless you understand how to do that for a hybrid MBR/GPT disk, I would say don't even think about it (and I have not tried it). Very easy to  make it unbootable.

Unfortunately, rEFIt and gptsync will put it back to 'normal' if gptsync is run.

An alternative is to reinstall or try cloning existing partitons again, to an external, re-partition, and get XP back in the MBR partion 3 or 4. XP is fussy about its partition position, see the triple boot installation info in 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

In any case, it depends on the existing partition numbering and ordering on the disk, the rEFIt partition inspector in OSX and gparted in Linux will show that. 

You just need to remove any of  OSX, ubuntu or swap from the fist 4 partitions, the EFI has to stay as #1.
  
There could be a simpler answer, but I dont know it.

---

