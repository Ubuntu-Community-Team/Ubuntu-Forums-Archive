---
title: "[SOLVED] reinstalling with gutsy gibbon help."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by mark. on 2007-11-13
so i've decided to uninstall ubuntu from my computer, because it won't even run ([unsolvable resolution issues :/]("http://ubuntuforums.org/showthread.php?t=561500"))

and since i am still a linux fan, i might as well start clean with a new os. so heres the help i need--

1. how do i uninstall ubuntu, and restore the partition to my WinXP again? 
2. if i install ubuntu 7.10, is there any way to share the partition with my winxp files so that i can access both files form either os? (one of my main problems before)

---

### Post by Duck2006 on 2007-11-13
1)

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

2)
Not sure of that one.

---

### Post by mysticrider92 on 2007-11-13
1) The [gparted live cd]("http://gparted-livecd.tuxfamily.org/") is the easiest way to give XP the space again. Just boot it up, delete the swap and ext3 partitions (do not delete any NTFS or FAT32 partitions!!), then resize the NTFS to fill the rest of the space on the drive.

After you do this, your MBR will have a problem, as Grub is there, but the files are not. To fix this, you will need to boot an XP install disk. Go into Recovery Console, and type "fixmbr". Your computer should be back to how it was before Ubuntu.

2) There are programs for both Ubuntu and XP to access files on either one, but a more stable option is to create a FAT32 partition for all of your data. This can be read by both OS's easily.

If you want to do this without an extra partition, you will need the ext2-IFS program for XP. Ubuntu 7.10 can read NTFS partitions out of the box, so you don't need to worry about it.

---

### Post by mark. on 2007-11-13
wait, so 7.10 can already read all hard drive partitions?
or is there an installation option where i dont have make a new partition, but just use the partition i have already?

---

### Post by mysticrider92 on 2007-11-13
It should read the partitions like it is, but it might not work all of the time.

If you want to install without making a new partition, you will have to use the manual partitioner on the install cd.

---

### Post by mark. on 2007-11-13
ok i am running on my boot cd as of now, but i just wanna make sure--
i'm going to delete my 2nd partition (old non-working ubuntu) while in the partition manager. then i create a new partition using manual, and the partition type should be fat32, right?

wanna make sure before i install this, ty for your help

---

### Post by charleseddy on 2007-11-14
Honestly, as far as partitions, I disagree with the others.  You can delete your old ubuntu, no problem.  Then, install 7.10 on top of the blank space.  7.10 reads NTFS (windows xp and windows 2000) partitions without problems, so no worries there.  For windows, you can install this really simple-to-use program called Ext2 IFS (fs-driver.org), which will allow you, if you follow the really easy instructions they give you in the windows installation, to read Linux ext partitions.

Stability isn't really an issue at this point, because it seems as if they've worked those issues out both from the Windows side (being able to run ext partitions) and the ubuntu side (being able to run ntfs partitions).  Hope this helped, ce.

---

### Post by mark. on 2007-11-14
yesthank you everyone for your help. i will be installing 7.10 soon.

ubuntuftw

---

