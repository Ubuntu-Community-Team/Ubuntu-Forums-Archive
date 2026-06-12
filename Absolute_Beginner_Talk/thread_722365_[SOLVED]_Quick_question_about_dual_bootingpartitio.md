---
title: "[SOLVED] Quick question about dual booting/partitions"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Helios1276 on 2008-03-12
(bearing in my I aint too tech savvy)

So far ,whilst talking to people about setting up my dual boot, I've been told about issues with windows and ubuntu reading from a selected partition set up to share ( e.g music, video). Poeple have talked about ntfs and that but my xp is telling that i have a FAT32 file sytem..is this any bearing or am i getting confuzed ..again lol 

HD: 80gb 5400rpm SATA hd ( if needed)

Cheers in advance!

---

### Post by Helios1276 on 2008-03-12
lol im guessing i asked a terrible question without research, off to google i go

---

### Post by SpaceTeddy on 2008-03-12
fat (and fat32) is the old filesystem that used to be used up until windows 2000. Both, linux and Windows can read it. Ubuntu will give you access to any fat32 partition you have when you are installing it. If in doubt, run the live-cd and see if the drive appears (which it should)

As for ntfs, that is the windows filesystem since windows 2000. It used to be a problem accessing it in Linux, but since the ntfs3g drivera, this is not a problem anymore. As far as i know, gutsy brings these drivers by default and will also give you access to any ntfs drive it finds by default.

If you are in windows, however, you will not be able to access the linux partition - since windows does not support the standard ubuntu filesystem (ext3). there are drivers out there to access it, tho. 

hope this answers you question... a little :)

---

### Post by xravexheavenx on 2008-03-12
Oops...  Misread and made irrelevant reply.  Mods, please delete.

---

### Post by Helios1276 on 2008-03-12
cheers man , it does! however now im wondering why a laptop i bout (new) last year loaded with xp and being (apparently vista ready) has fat32 in it??? i guess i should be happy with this and my proposed feisty fawn/xp combo ..ive no idea lol

---

### Post by SpaceTeddy on 2008-03-12
preloaded os usually from some distrubutors come with a prepackaged fat32 drive which should get converted upon first boot of the customer. This is usually done since some programs get run during the first boot which cannot read/write ntfs. I know this is/used to be the case with IBM/Lenovo Laptops.

you can always convert your filesystem - there is a button somewhere in the accessories in windows for it... i think :)

also, recovery partitions usually run on fat32... but you should not be able to see them

---

### Post by Helios1276 on 2008-03-12
not too sure , well while defraging it says FAT32 and under my computer-acer:c (or other side acer:d) - properties it says FAT32 also. the laptop is a year or so old , should i wonder/worry /care?

---

### Post by SpaceTeddy on 2008-03-12
don't think you should worry about it too much - it works, doesn't it ?

---

### Post by Helios1276 on 2008-03-12
true it crashes, locks up and fragments just as much as my other friends on xp lol thanks for the info

---

### Post by Edoaigor on 2008-03-12
> **Helios1276 said:**
> cheers man , it does! however now im wondering why a laptop i bout (new) last year loaded with xp and being (apparently vista ready) has fat32 in it??? i guess i should be happy with this and my proposed feisty fawn/xp combo ..ive no idea lol
Might not be too proficient with ubuntu but I can answer that.. some thought that installing XP on a FAT32 partition would make it stabler, faster and less incline to fragmenting system files. Some believe that chewing raw garlic keeps you from catching the flu...but whatever.
FAT32 however is NOT the native filesystem for XP and more than once this wise stunt has led to data loss.

---

### Post by A$h X on 2008-03-12
FAT32 is limited in that you can't have a single file of size 4gb or above. Convert your partition to NTFS, and then you can have a shared data partition like me, so both windows and ubuntu can access your mp3, movies etc!

---

### Post by Helios1276 on 2008-03-15
so from ubuntu I can set up say a 20g partition in ntfs ?

---

### Post by jprophet420 on 2008-03-15
yes, but not on your existing windows instalation. you have to reinstall windows to change the file system its written to.

---

### Post by SpaceTeddy on 2008-03-15
i am lost here. first off, as far as i know, ubuntu can access fat aswell as fat32 and ntfs. so converting to ntfs to access the drive is not a must. 

The advantages of ntfs lie mainly in how it handles the files and file allocation tables. While Fat and Fat32 use one main table (and hopefully also a backup somwhere), ntfs is distrubuting the backup up the structure a lot besser (maybe it even uses journaling by now...), i.e. being more resistant to crashed and other failures.

as for creating a partition for windows - no, you do NOT need to delete anything from your drive, and you do NOT need to reinstall your windows. Windows brings it's own converter tool to change a running fat32 filesystem into a nfts drive. Also, ubuntu can create ntfs partiton and drives (mkfs.ntfs) which will be automaticially picked up by any windows that supports ntfs upon next boot.

essentially - on a new drive, ubuntu can create a ntfs partiton that windows can read.
ubuntu cannot convert the existing fat32 partiton of windows into nfts - but if you run the windows, it can do that.

---

### Post by Helios1276 on 2008-03-17
Cheers man, thread solved I'd say!:)

---

