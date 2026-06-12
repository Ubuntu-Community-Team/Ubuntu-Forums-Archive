---
title: "Problem adding 2nd hd to samba network"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by lapinoid on 2008-01-12
After following this useful advice ginven under
bit-tech.net 
I was finally able to get my xubuntu fileserver running! (even though it cost my easily more then 2 hours as promised ;-))
I have a 14 GB Hd in my PIII server and put an additional 320 GB in. partined it with gparted, formatted it as ext.3 and mounted it. So far so good. I can put the data up from the 14 Gb Hd, but cant´acces it from the Windows clients. I tried to find it under the system tray "shared folders" but was unable to come up with a solution. 
Maybe someone has an idea how to overcome this problem! My mp3 collection is already waiting to "mount" the 320 GB :-)

Thx
Lapinoid

---

### Post by naugiedoggie on 2008-01-12
> **lapinoid said:**
> After following this useful advice ginven under
bit-tech.net 
I was finally able to get my xubuntu fileserver running! (even though it cost my easily more then 2 hours as promised ;-))
I have a 14 GB Hd in my PIII server and put an additional 320 GB in. partined it with gparted, formatted it as ext.3 and mounted it. So far so good. I can put the data up from the 14 Gb Hd, but cant´acces it from the Windows clients. I tried to find it under the system tray "shared folders" but was unable to come up with a solution. 
Maybe someone has an idea how to overcome this problem! My mp3 collection is already waiting to "mount" the 320 GB :-)

Thx
Lapinoid

Hello,

Something of a guess, but if it is a P3 then it's likely that the BIOS is not recognizing the whole drive.  Even with LBA, those old systems had pretty low size limits for HD recognition.  I have a P4 950MHz system that had a drive go bad and I replaced it with a 250GB drive.  Windows will only see the first 100GB, although linux will see the whole thing.  I think the limit may be even lower for a P3.

If that is what is happening to you, then your only option is to use just the first bit of the drive.  You should be able to look in the BIOS setup or at the POST boot messages and see what size drive it is reporting, that is all Windows is seeing.  Partition the drive at that point and then Windows will see it.

Also, it might go without saying but I'll say it anyway:  be sure you have the most recent BIOS upgrade, as that can affect the size of the drive that the BIOS will see.

Thanks.

mp

---

