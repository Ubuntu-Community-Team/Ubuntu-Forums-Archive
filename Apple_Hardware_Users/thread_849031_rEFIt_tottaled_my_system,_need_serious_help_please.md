---
title: "rEFIt tottaled my system, need serious help please"
date: 2008-07-04
forum: Apple Hardware Users
---

### Post by ghost739 on 2008-07-04
Alright, so I used the install guide for a triple boot system on the webpage [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I think I did everything right up to step 5: (click advanced and change where grub is going to be installed)

I had so many choices and only two of them made sense, so I installed it on a random sda#. When I finally installed Ubuntu, I restarted and could only see the MacOSX partition. Thought that was normal.

The automatic rEFIt install did not work, so I installed it manually. After that, I could still only boot to MacOSX because a black screen would come up and say that there is no bootable device - please insert cd.

I deleted the efi folder in macintosh hd and chose my startup disk as mac osx.

I restarted and could not see anything but a white screen. I could not boot from anything. I managed to get in by inserting my install disc somehow.

Here are my results from partition inspector:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    151495231  Mac OS X HFS+
 3      151495232    226901482  Basic Data
 4      226902056    312581767  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    312581807  ee  EFI Protective

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: GRUB
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 151495232:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 226902056:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data

--

I'd really like to boot to all three, but if I've screwed up please tell me how I could restore my system back to normal. I have a Mac and Windows backup on my external harddrive.

Thanks so much,
John

---

### Post by ghost739 on 2008-07-04
Okay umm... I fixed the boot menu problem. It only shows MacOSX, and I think all I have to do is get rid of the Ubuntu partition to restore it back to normal, but I still could use some help getting rEFIt to work properly.

---

### Post by umbrAtrorum on 2008-07-04
how did you solve the boot issue?

---

