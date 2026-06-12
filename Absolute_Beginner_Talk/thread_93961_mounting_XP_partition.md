---
title: "mounting XP partition"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2005-11-23
In my first few days on Ubuntu I managed to mount my XP partition. It hasn't remained mounted and I can't find the simple way I managed to do it the first time.

I know I can work out how to do it again with enough reading, and I am continually reading bits and pieces, but I'd appreciate a quick heads up on mounting my XP partition and would love a quick lesson on either keeping it mounted, why it won't stay mounted (if it won't) and if not how to mount it quickly on boot.

I'm a beginner in Linux but not a total computer newbie. I WILL ask more questions so I don't expect a complete answer in one post. I expect to have to find out more, but just wanted a bit of a grounding.

---

### Post by jorn on 2005-11-23
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by Pablo_Escobar on 2005-11-23
1. You need to know what is the name of the partition You want to mount
2. You need to know what file format it is in (FAT32 or NTFS)

You can do this both by executing a command:
> fdisk -l
in the terminal.
Paste the contents here so we can proceed :)

---

### Post by mdsmedia on 2005-11-23
thanx jorn and Pablo....

it is an NTFS partition. I'm just wanting to mount it at this stage. Soon I want to make a fat32 partition to be read and written by both systems. Then I want to remove the NTFS partition (not naming names)...right now all I want to do is mount the NTFS partition so I can READ the files.

---

### Post by Pablo_Escobar on 2005-11-23
Then Jorns link is the correct one.
[http://www.ubuntuguide.org/#automountntfs]("http://www.ubuntuguide.org/#automountntfs")
If You need assistance post what "fdisk -l" spits out

---

