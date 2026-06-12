---
title: "Formatting External Hard Drive"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by notaloafer on 2007-07-26
Hard Drive: Western Digital 120GB

All I want to do is format it with a file system thats compatible with my three different computers I'm backing up:
Windows 2000 Professional (mail server/other stuff)
Ubuntu Linux (web server)
Windows XP Home Edition (my laptop for personal use)

Which file system should I use? Also what can I use to format it? I was thinking FAT or FAT32, but Windows XP won't let me format in that (it only lets me do NTFS because like all other Microsoft OS's, it sucks :P).

The main thing I need this for is my laptop and linux server. The problem with NTFS is linux is having problems writing to it.

Any help would be greatly appreciated :)
I don't really want multiple partitions, just one big one with seperate folders for the different computers.

Thanks!
-Eric.

---

### Post by wolfen69 on 2007-07-26
windows should give the option to format as FAT. but it's been a while for me.   ultimate boot cd [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)  should have some formatting utils.

---

### Post by Ek0nomik on 2007-07-26
I'd use FAT32 if you want data to come from Windows and Linux.  This way both of your operating systems can read and write to the disk out of the box.

Partition Information:

[http://support.microsoft.com/kb/313348](http://support.microsoft.com/kb/313348)

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/choosing_between_ntfs_fat_and_fat32.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/choosing_between_ntfs_fat_and_fat32.mspx?mfr=true)

You can also use software to do it graphically like Partition Magic for Windows.

---

### Post by notaloafer on 2007-07-30
I attempted formatting in FAT32 but when I plug the HDD into linux, it shows a shitload of random character folders, etc. and it still cannot write to the disk. Any other ideas? Maybe the program I'm using on windows is messed up, but I don't think so (the HDD works on windows with fat32 system).

Whats a good formatting utility for linux? or a good program for windows to format to fat32?

---

### Post by oilchangeguy on 2007-07-30
are you using a factory restore cd, or a windows only cd? because you will have the option to use fat32 with a windows only cd.

---

### Post by notaloafer on 2007-07-30
Iguess i can try using my windows cd.

---

### Post by oilchangeguy on 2007-07-30
> **notaloafer said:**
> Iguess i can try using my windows cd.

just use the windows product key, from the sticker on the computer. and you'll be ok.

---

### Post by notaloafer on 2007-07-30
It didn't work. My install CD will only let me format in NTFS quick or NTFS the long way. Isn't there just a program I can use out there thats linux or windows based??? It's driving me nuts to complete such a simple task :P

Thanks
-Eric

---

### Post by pistcivet on 2007-07-30
Windows XP only lets you format to FAT32 if the partition is less than 32 GB.
Not sure about Win 2000.

Have you tried installing gparted and formatting it to FAT32?
That would probably be the easiest way.

You could also format with the command line.
see: man mkfs.vfat

How do you have this drive partitioned?

Edit: You mean you have to format this drive under Windows?
If your web server has no gui, you can still get this accomplished via the terminal.
You could use the server and the "parted" and "mkfs.vfat" commands.

---

### Post by notaloafer on 2007-07-30
The hard drive right now is completely wiped, and thus I have no backups right now of anything (I need to get this working!! lol). So I'm willing to format it any way that will work.

---

### Post by pistcivet on 2007-07-30
Do you have access to the server? Like is it in the same room with you?
Does it have a monitor and keyboard attached?

Would you be able to plug the drive in and use it to partition/format?

I don't think I can walk you through the whole process, but first you plug the drive in
and type dmesg
the last few lines will tell you where the drive is assigned. might be sda
In which case you'd type parted /dev/sda

You'd have to read man parted and man mkfs.vfat before you start.

---

### Post by notaloafer on 2007-07-30
gparted worked fine.
and yes, my server is in my room right next to me :P

Thanks for the support guys!
-Eric

my issue is resolved, for any others that have problems with this, Gnome Partition Manager works great.

---

### Post by ev5unleash1 on 2007-07-30
I would just say put 2000/XP on the internal HDD and Ubutu on the external.

Or just partition the external. But watch out you can only make up to 4 partitions on Ubuntu.

---

### Post by pistcivet on 2007-07-31
Glad to hear it **notaloafer**.
I thought you were stuck in a command line.
But since I racked my brain trying to remember this, I'll post it anyway.
Just in case any masochists want to do it in CL.

Say the disk is at /dev/sda (and not mounted)

```
sudo parted -i /dev/sda
mklabel msdos
mkpart primary 0% 100%          (makes 1 primary partition span entire disk)
mkfs 1 fat32                    (puts a FAT32 filesystem on that partition)
quit
```
Then you should reformat the disk and check for bad blocks (unmount first if necessary)
```
sudo mkfs.vfat -c -L label -F 32 /dev/sda1
```
label can be anything you want up to 11 characters, no spaces.
If you want to go nuts with the check, specify -c twice,
that will write/read 4 bit patterns to the entire drive, giving it a real workout.
(takes a really long time)  :popcorn:

---

### Post by oilchangeguy on 2007-07-31
> **pistcivet said:**
> Windows XP only lets you format to FAT32 if the partition is less than 32 GB.
Not sure about Win 2000.

Have you tried installing gparted and formatting it to FAT32?
That would probably be the easiest way.

You could also format with the command line.
see: man mkfs.vfat

How do you have this drive partitioned?

Edit: You mean you have to format this drive under Windows?
If your web server has no gui, you can still get this accomplished via the terminal.
You could use the server and the "parted" and "mkfs.vfat" commands.

not true! i'm currently useing my sisters acer aspire 5000 laptop, running xp home, and for some reason acer takes an 80gb hard drive, splits into two partitions, and formats it fat 32.

---

### Post by pistcivet on 2007-07-31
> **oilchangeguy said:**
> not true! i'm currently useing my sisters acer aspire 5000 laptop, running xp home, and for some reason acer takes an 80gb hard drive, splits into two partitions, and formats it fat 32.
"You cannot format a volume larger than 32 gigabytes (GB) in size using the FAT32 file system during the Windows XP installation process."
Source:
[http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

I guess thats what I was remembering.
I don't know what the size limit is after XP is installed.

Also, for Win 2000:
"You cannot format a volume larger than 32 GB in size using the FAT32 file system in Windows 2000. The Windows 2000 FastFAT driver can mount and support volumes larger than 32 GB that use the FAT32 file system (subject to the other limits), but you cannot create one using the Format tool. This behavior is by design. If you need to create a volume larger than 32 GB, use the NTFS file system instead."
Source:
[http://support.microsoft.com/kb/184006/](http://support.microsoft.com/kb/184006/)

---

