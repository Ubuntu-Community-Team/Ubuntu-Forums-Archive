---
title: "LiveCD: saving data to where?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by rodinia on 2007-10-03
Hello again,

I do have a liveCD now 
*grrr* my boyfriend downloaded the latest version where I cannot store installation data on a usb stick, and that was the last CDRom we had. Anyway, ubuntu runs smoothly at least. So I understand that Ubuntu uses a different file system than windows. Please can someone explain to me why I can open about everything on my harddisk but don't save anything to it? I only get the message //drive does not exist while I'm looking right at it.Would it still be an option to change the file system on a USB stick and save the data to it and would this data be accessible under windows as it is vice versa?

I want to test a scanner but this whole thing is rather useless when I cannot save the scanned images and check the quality under windows with a software developped for analysing certain aspects within the scanned images. 

Rod.

---

### Post by tszanon on 2007-10-03
You can't save anything to the disk probably because the partitions are all formatted as NTFS. Ubuntu, by default, can't write to NTFS partitions. You must use a special program called ntfs-3g to be able to write to NTFS partitions.

About the USB stick: if it's formatted as FAT, both windows and ubuntu can read/write to it without any problems.

---

### Post by rodinia on 2007-10-03
How do I know if a USB is FAT formatted besides trying? I can see myself at the office tomorrow, feeling all embarraced because my 'brilliant idea' is not working (not that colleagues have better ideas). Is a USB stick FAT formatted by default or how could I change that? Sorry for asking, but I'm really not good with computers.

Rod.

---

### Post by Dr Small on 2007-10-03
Open Gnome Partition Editor (Gparted), and select your USB drive, (while it is plugged in).
You will be able to see what filesystem it is then, and also be able to reformat it to any filesystem you like.

Dr Small

---

### Post by rodinia on 2007-10-04
> **Dr Small said:**
> Open Gnome Partition Editor (Gparted), and select your USB drive, (while it is plugged in).
You will be able to see what filesystem it is then, and also be able to reformat it to any filesystem you like.

Dr Small

Al right. Will do that. Well, I realised I can see that in Windows as well. So my USB stick seems to be FAT formatted. On Wikipedia I found there's a difference between FAT and FAT32 *sigh* But I'll try to use my stick in Ubuntu once I'm at the office and hope it'll work. 

Rod.

---

### Post by UbuntuniX on 2007-10-04
> **rodinia said:**
> Al right. Will do that. Well, I realised I can see that in Windows as well. So my USB stick seems to be FAT formatted. On Wikipedia I found there's a difference between FAT and FAT32 *sigh* But I'll try to use my stick in Ubuntu once I'm at the office and hope it'll work. 

Rod.

It can be FAT16 or FAT32, but if you purchased it in the last few years I'm sure it's FAT32.

---

### Post by rodinia on 2007-10-04
> **UbuntuniX said:**
> It can be FAT16 or FAT32, but if you purchased it in the last few years I'm sure it's FAT32.

Yes, I bought it quiet recently. Is FAT32 good or bad for my needs? Meaning, do I have to make a backup and reformat it or can I just use it?

---

### Post by UbuntuniX on 2007-10-04
> **rodinia said:**
> Yes, I bought it quiet recently. Is FAT32 good or bad for my needs? Meaning, do I have to make a backup and reformat it or can I just use it?

The file system on it isn't too important. But if you want to install Ubuntu on it, it's best to format it with ext3.
Ubuntu should be able to read files on it regardless, though I'm not sure about writing.

---

### Post by rodinia on 2007-10-04
> **UbuntuniX said:**
> The file system on it isn't too important. But if you want to install Ubuntu on it, it's best to format it with ext3.
Ubuntu should be able to read files on it regardless, though I'm not sure about writing.

Right. I don't want to install Ubuntu on it but I'm looking for a way to save data (scanned images) using just a liveCD and move the files over to Windows somehow.

Rod.

---

### Post by lgcabarcas on 2007-10-04
you'll be all right with your USB stick just the way it is now, both OS have read write acces to it on it's current state ;)

---

### Post by mivo on 2007-10-04
> **rodinia said:**
> Right. I don't want to install Ubuntu on it but I'm looking for a way to save data (scanned images) using just a liveCD and move the files over to Windows somehow.

Yes, this will work just fine if it is FAT32 formatted. :) It's not an impressive file format for a hard drive, but for an USB stick used by both Linux and Windows (or MacOS), it is just fine. You don't need to format it.

---

### Post by dkaddict on 2007-10-04
My USB drives are either FAT16 or FAT32. I don't have Windows in any form on my laptop but keep these with the ntfs file systems because Ubuntu doesn't access them any differently than, for eg, my ext3 /home partition. All of the data in my USB drives is data gathered and used in Ubuntu. Again, this data can be read and amended just like data in my hard drives.

If you are running your Ubuntu from a Live CD environment only you may want to give SLAX a try. With SLAX you can save system settings to, for instance, a USB drive or a small partition on your HDD. The Ubuntu live CD is good but you will benefit more from having a hard install of Ubuntu somewhere on your HDDs. 

Dual booting with Win and Ubuntu is easy and there are loads of how2s on the net. Once installed on a dual boot set-up, accessing, reading and writing to data on your NTFS Windows partitions is no different to doing all of the same in the native Ubuntu environment. Also, many Windows apps will run in an Ubuntu set up if WINE is installed. Again, the full benefits of Ubuntu can't be had from a Live CD environment only.

peace

dk

---

### Post by funpop on 2007-10-04
ntfs-3g is installed by default in gutsy gibbon (latest, so thats what you got???)

when you run the live cd your windows partitions (ntfs) are mounted as read only, means you cant write to them. 

usb-sticks should mount with write access, so you should be able to store whatever you want there..

---

