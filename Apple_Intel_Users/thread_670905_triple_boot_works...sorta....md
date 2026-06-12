---
title: "triple boot works...sorta..."
date: 2008-01-18
forum: Apple Intel Users
---

### Post by dexter750 on 2008-01-18
finally got ubuntu on my macbook pro (so glad)
but i need windows (xp sp2) to play my games and run autocad

i have 4 partitions (osx hfs, ubuntu ext3, windows ntfs, swap)
im running rEFIt 

i was messing around for a long time trying to get this all to work, as i had originally installed windows via bootcamp and i wanted to reclaim some of that space to use for ubuntu

well i finally got it to work, knocked back 8 gigs for space for ubuntu, installed, works fine. loads from grub.

now when i try to get into windows though, im getting that lame ' hal.dll ' is corrupt error, even though ive replaced it with a good copy many times.

windows is also loading through grub. 
i havent tried reinstalling windows from CD yet though, but ive read that people have tried that but then windows just complains about an unbootable mount volume. cruds. i'll try it myself as soon as i can get my hands on a install CD. 

any other ideas?
thanks

---

### Post by cyberdork33 on 2008-01-18
If you installed grub to the MBR (like it wants to by default) then you could try booting the windows disc into recovery mode and using the fixmbr command. Then reinstall grub to the Ubuntu root partition instead of the MBR.

See the link in my signature for a how to.

---

### Post by dexter750 on 2008-01-19
thanks much for the link. i followed the post and it fixed my setup a little better. windows no longer loads through grub, but i am still getting the hal.dll error. ubuntu and os x still load fine.

once i did the grub stuff, i did recovery console and fixmbr. it didnt seem to do anything. is grub still in the mbr or something?

i did a windows repair install. still got the hal.dll error. damn you hal, damn you.

---

### Post by dexter750 on 2008-01-19
hmm.... could it be because i actually have 6 partitions (i forgot about linux swap and some EFI partition) and the NT/XP bootloader can only support 4?. I tried to do a fresh install of windows by removing its partition and trying again, but i was told i was over the limit for partitions. 

or is the limit of 4 partitions a BIOS thing?

btw, heres my GPT and MBR tables
```

Parted (GPT):
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
        17.4kB  20.5kB  3.07kB  Free Space                              
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   86.1GB  85.9GB  hfs+         Merged_Untitled            
        86.1GB  86.2GB  134MB   Free Space                              
 3      86.2GB  110GB   24.2GB  ntfs         Untitled 2                 
        110GB   110GB   807kB   Free Space                              
 5      110GB   111GB   300MB   linux-swap                              
 4      111GB   120GB   9295MB  ext3                                    


Fdisk (MBR):
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10461045

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       10469    83886080   af  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   *       13464       14594     9077148+  83  Linux
Partition 3 does not end on cylinder boundary.
```

---

### Post by cyberdork33 on 2008-01-20
> **dexter750 said:**
> once i did the grub stuff, i did recovery console and fixmbr. it didnt seem to do anything. is grub still in the mbr or something? Yes stage1 of grub is installed in the mbr by default. my uide shows you how to move that to the Ubuntu partition rather than the mbr so that the windows bootloader can reside there.

> **dexter750 said:**
> hmm.... could it be because i actually have 6 partitions (i forgot about linux swap and some EFI partition) and the NT/XP bootloader can only support 4?. I tried to do a fresh install of windows by removing its partition and trying again, but i was told i was over the limit for partitions. 

or is the limit of 4 partitions a BIOS thing?
The 4 partition limit is imposd by windows because it cannot read the true GPT, but rather the legacy partition table in the MBR.

I am going to guess that those small free space sections might be giving windows trouble. Sorry that the hal.dll error isn't getting fixed for you. It may not be repairing correctly because of those free space sections as well. and actually fdisk doesn't even see the ntfs partition at all. Maybe you need to sync the tables in the refit menu?

---

### Post by dexter750 on 2008-01-23
thanks man, i been messing around with this for a bit now. hunkered down and paid for ipartition3 because i got tired of trying to do it the hard way. 

...had to do alot of synching with the GPT/MBR tables in rEFIt, because i was playing with different partition combinations to see what would get windows to work.

first made 4 partitions
EFI, OS X, Linux, XP (i read XP likes to be last on the partition table)

installed windows fine
installed ubuntu (added 5th partition, swap, after windows), did not know how to make it install grub without messing up the MBR, so kinda screwed there again. i tried to mount it in the Ubuntu partition but it wouldnt work for some reason. 

after getting screwed on the MBR again, i did fixmbr on partition 4 and fixboot and then i had to modify the boot.ini to point to partition 4. windows is loading again.

did the steps in your guide again, all is booting fine. 
frickin awesome!!


[SIZE="1"]now i need to find the bootcamp drivers [/SIZE] ;) :-\"

thanks so much dude.

---

### Post by smocksturr on 2008-01-24
wow, i have the identical problem.
i'm going to try that guide.

---

