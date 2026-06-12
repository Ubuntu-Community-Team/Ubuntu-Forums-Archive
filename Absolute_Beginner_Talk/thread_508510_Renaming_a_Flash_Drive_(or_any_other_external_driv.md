---
title: "Renaming a Flash Drive (or any other external drive)?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by SendDerek on 2007-07-24
Hello!

I just bought a USB flash drive and I would like to rename it to something a little more personable than "disk".  As a comparison, in Windows, you can right click on the drive and rename it to say "My Jumper".  Then when you load it into any computer (windows, mac, or linux alike) they will recognize it as "My Jumper" and automatically mount it as such.

Is there a way to do this in Ubuntu?  I tried to simply open "Computer" and rename it there, but it came up with an error message saying that it couldn't be renamed.

Thanks in advance!

-Derek

---

### Post by laidback on 2007-07-24
Is this any good?

In a terminal

mount (to see sda definitions)
sudo e2label /dev/sda? newlabel

The mount command is used to find the sda number e.g. sda1
Enter that number in the second line in place of the ?

Never tried to see what Windoz makes of it.

---

### Post by airtonix on 2007-07-24
if your not sure about doin this in LInux(ubuntu).

then use the fdisk tool with windows.

or use the format gui tool in windows.

both will prompt you for a volume name when formatting said disk

---

### Post by Orochi on 2007-07-24
Yeah in Gparted it lets you name the different partitions, but I don't know if you can change the name of an already formatted drive that way.

---

### Post by laidback on 2007-07-24
My understanding of Gparted is that it lets you name a drive rather than each partition....but then I could have misunderstood the options.

---

### Post by NaturalScience on 2008-02-28
Format the drive - run mkfs.<fs>, <fs> = whatever file system you want.  For me I like having my flash drive be FAT32 so it can used cross-platform.  Make sure there is no valuable data on the drive, then run

mkfs.vfat -n <new_volume_name> /dev/sdb1 (or whatever it's called when checking it with an fdisk -l)

---

### Post by cbtengr on 2008-02-28
In XP, just open My Computer, right click on the flash drive and select "Rename".  No need to reformat.  I do this all the time with flash drives and cards from my digital cameras.  This name will appear when mounted in Ubuntu.  Don't know how to do this in Ubuntu, sorry.

---

