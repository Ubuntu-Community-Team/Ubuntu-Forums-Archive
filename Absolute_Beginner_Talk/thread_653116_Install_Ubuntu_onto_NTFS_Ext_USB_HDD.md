---
title: "Install Ubuntu onto NTFS Ext USB HDD"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by sulpherdragon on 2007-12-29
Hi guys, my first post here.

I need to install Ubunto onto my external harddrive but I need to keep it NTFS. Theres no problem formatting it or anything, theres nothing to lose on it. But im going to be using Windows on my internal hard drive to transfer large files (10gb+) onto it so I need it to be NTFS.

I intend installing Gutsy Gibbon onto the full portion of my 250GB ext drive.

Suggestions and help appreciated.

---

### Post by taurus on 2007-12-29
You cannot install Ubuntu on a ntfs filesystem.  On the other hand, XP can read and write to ext3 just fine with fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by sulpherdragon on 2007-12-29
Thats a little unfair :(

I thought that Gutsy Gibbon understood NTFS, obviously not to the extent I thought. Will it only install to EXT3?

---

### Post by hums07 on 2007-12-29
Gutsy understand NTFS, but GRUB might not. CMIIW.

---

### Post by taurus on 2007-12-29
Gutsy understood ntfs filesystem alright and in fact, it would even let you write to it.  BUT ntfs filesystem doesn't understand about ownerships and permissions like Unix/Linux is intended.

---

### Post by sulpherdragon on 2007-12-29
Well I can resort to partitioning, Does 20gb ext3 and a 230gb ntfs sectioning sound good? Obviously having the ext3 on the first side of the disk.
Can you guys forsee any problems with that?

---

### Post by gn2 on 2007-12-29
> **sulpherdragon said:**
> Well I can resort to partitioning, Does 20gb ext3 and a 230gb ntfs sectioning sound good? Obviously having the ext3 on the first side of the disk.
Can you guys forsee any problems with that?

Are you going to have a single or dual boot?

Which OS will you use the most Linux or MS?

What I'm trying to get at is why you want to use the NTFS file syatem.

---

### Post by sulpherdragon on 2007-12-29
Im sure NTFS isint specifically required, however i intended using the same hard drive to download large files (10gb+). I understand anything fat32 and lower wont accpet 4gb+ files. I have xp on my internal hard drive which i use for games and downloading. I intended ubuntu to sit on my external drive which i download to. Whenever required i could boot to ubuntu OR plug the hdd into my laptop and boot ubunto from there. 
I was planning on using ubuntu as much as i can for programming, but i wanted to maybe boot to ubuntu on the laptop while someone used my main pc for games.

---

### Post by anagor on 2007-12-29
The setup you proposed will be no problem at all.
I have a full blown installation of kubuntu which takes only 3.5GB, so an ext3 partition with the size of 10GB will be more than enough I believe, as long as all other large files, like music and videos are stored on another partition, and in that case it can be ntfs if you need it to be.

---

### Post by logos34 on 2007-12-29
get fs-driver like taurus suggested, you'll be able to read and write to ext3 from windows just fine

---

### Post by sulpherdragon on 2007-12-29
My problem with the fs-drivers is this:

Its a portable hdd, I want to use it with my pc, my laptop, my friends pc, my college pc (which wont allow the drivers to install because of permissions). I know theres a solution out there, i think im edging towards the partition idea.

---

### Post by NullHead on 2007-12-29
I run xp x64 and on the page it says there is only x86 support. So I don't know if that will work for some.

---

### Post by sulpherdragon on 2007-12-29
all my computers are 32bit, the same with the college ones. i think i can deal with it not working on my friends 64bit. but thanks for reminding me.

---

### Post by sulpherdragon on 2007-12-29
Ok, im installing to the 20gb partition now. Ill keep you guys updated with the results

---

### Post by sulpherdragon on 2007-12-29
fatal error, grub cannot be installed.

Im a little worried now. trying again.

I think i set grub to install to hd0 instead of sda

---

### Post by gn2 on 2007-12-29
There are issues with installing Grub to a dual-boot with two hard drives with an OS on each, it can mix the drive and partition names up.

A simple method: If you want to install Ubuntu onto an external drive, disconnect the internal one before starting the process.

This will create a single boot Ubuntu system on the external drive, with the 20gb of Linux and the large NTFS data storage partition.

Order the BIOS boot order to have the external drive first in the list, then when you want to boot Ubuntu, just plug the drive in before booting, when you want to boot Windows from the internal drive, just unplug the external drive before booting.

After you boot into Windows you can plug in the external drive and it will be seen as a standard NTFS mass storage device.

---

### Post by logos34 on 2007-12-29
> **sulpherdragon said:**
> all my computers are 32bit, the same with the college ones. i think i can deal with it not working on my friends 64bit. but thanks for reminding me.

that's what I figured, which is why I didn't mention the x64 limitation (I run x64 XP so I can't use it).  

Now that you say you want to use the drive on a bunch of different computers, then multiple paritions is the way you want (have) to go

---

### Post by sulpherdragon on 2007-12-30
> **gn2 said:**
> A simple method: If you want to install Ubuntu onto an external drive, disconnect the internal one before starting the process.

Way ahead of you on that one, however im still having trouble with grub.

Ive tried installing it to the drive but most times i got an error such as "fatal error, grub-install failed" or something. but the last time i tried it it didnt give the error, seemed to work, but on booting from the hdd it says "cannot find operating system".

i gave it an ext3 partition of 18gb and a swap partition of 2gb, i left the rest unpartitioned. i got the fatal errors all the time until until i actually allocated a swap file (but i cant understand why that would fix it). now it dosnt seem to find grub. halp!

---

### Post by Niniel on 2007-12-30
You want to transfer files from XP to LInux?

In that case, just do a normal installation and copy the files from within LInux. 
Just make sure they are in a directory that's accessible, ie. nothing EFS encrypted or compressed. 
I've copied files both ways form Ubuntu, works like a charm, no problem at all.

---

### Post by sulpherdragon on 2007-12-30
> **Niniel said:**
> copy the files from within LInux. 

I wanted to create the files with windows software, movies and iso's, and store them directly onto the HDD. My software is currently set up to use the hard drive in this way. I dont intend to create them then transfer them onto the portable HDD, this would be too time consuming for the amount of stuff I deal with.

---

### Post by gn2 on 2007-12-30
> **sulpherdragon said:**
> Way ahead of you on that one, however im still having trouble with grub.

Ive tried installing it to the drive but most times i got an error such as "fatal error, grub-install failed" or something. but the last time i tried it it didnt give the error, seemed to work, but on booting from the hdd it says "cannot find operating system".

i gave it an ext3 partition of 18gb and a swap partition of 2gb, i left the rest unpartitioned. i got the fatal errors all the time until until i actually allocated a swap file (but i cant understand why that would fix it). now it dosnt seem to find grub. halp!

To be able to boot Ubuntu from the external drive, it will require a minimum of a / partition and a swap partition. (and the NTFS partition)

What software have you used to create the partitions? 
Was Partition Magic involved at any stage?

Have you tried re-installing Grub from a Live CD or a SuperGrub CD?
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

