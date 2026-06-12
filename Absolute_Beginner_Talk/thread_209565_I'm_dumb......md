---
title: "I'm dumb....."
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Hubris67 on 2006-07-05
OK, just installed Ubuntu this week. Trying to change the permissions on one of my drives. Just a media drive and I need to be able to write to it. Went through most of the chmod tutorials but still can't figure this out. Tried it through the GUI but all my choices are greyed out. Used chmod -l to see permissions and was going to try chmod =rwx,g+s file, but the command list I was referencing said something about this command turning on the 'set group-ID'? I know I'm being monumentaly dumb, but I need some advice. Oh, background.....I have windows installed on one drive, and Linux on the other. The drive I'm trying to be able to write to is the larger partition of the drive without Windows on it where I've installed Ubuntu. Thanks for anything you can give me.

---

### Post by T700 on 2006-07-05
1.  Don't call yourself dumb.  There are plenty of people eager to beat you up; no sense in helping them.  Plus, a more descriptive subject line will get you more and better responses.

2.  I'm not entirely clear--is this a thumb drive or the like?  What file sytem is the drive in question?

Paul

PS.  Welcome to the forum!

---

### Post by _simon_ on 2006-07-05
personally I install the nautilus scripts via Automatix. This gives you the option of opening files and folders as root which means you can change permissions / edit files on the fly. (assuming you use GNOME that is)

---

### Post by Bloch on 2006-07-05
Go to System > Administration > Disks

Is the partition you want to write to shown? Does it have a filesystem?

---

### Post by Hubris67 on 2006-07-05
Heh, ok sorry. It's an NTFS file system. Read some stuff that said changing permissions on this was a little tricky if not dangerous.

---

### Post by cowley on 2006-07-05
you cannot by default write to an ntfs disk, there is a program that allows you to do this though i cant think what its called.  do some searches within the forums and you will easily find out.  do you need it to be ntfs? it would make sense to convert it to ext3 if possible.

simon

---

### Post by T700 on 2006-07-05
[quote=Hubris67]Heh, ok sorry. It's an NTFS file system. Read some stuff that said changing permissions on this was a little tricky if not dangerous.[/quote] 
That's the problem.  Linux can read NTFS, but not write to it (or delete, which is another form of writing).  There are certain work arounds that attempt to reverse engineer MS's closed source file system, but I would **not** trust any important data to them.

If you have to have read/write for both Linux and Windows, you could format the drive for FAT32.

Paul

---

### Post by MaximB on 2006-07-05
Do NOT change premissions on this drive !!!
ubuntu can't write to NTFS and all the programs that "let" you write into NTFS are very dangerous and unstable - they can make your NTFS drive unreadable at all.
if you want to share this drive with linux/winxp convert it to fat32 or to ext3
with ext3 - you can download a small program that will make ext3 partition writable and readable on winxp.

---

### Post by Arathorn on 2006-07-05
How do I convert an NTFS drive into Ext3? I have my Ubuntu partiton succesfully mounted in Windows and now I want to do the same with my -now- ntfs data partition. But in gparted I don't see that option.

---

### Post by someusernoob on 2006-07-05
Its not possible to convert NTFS to ext3 as far as i know. Best way is to back up the data on the disk and format it to ext3 (you'll loose all the data).

---

### Post by Frank Golden on 2006-07-05
[QUOTE=someusernoob]Its not possible to convert NTFS to ext3 as far as i know. Best way is to back up the data on the disk and format it to ext3 (you'll loose all the data).[/QUOTE]
Or convert it to Fat 32 using Windows . Remember that you can't have any file any larger than 4GB on a Fat 32 drive. If you have another drive to back it up to that is what I would do rather than converting it.

---

### Post by Hubris67 on 2006-07-08
Allrighty, so what I'm hearing is there's no safe way to fix this without reformatting the whole drive and re-partitioning it after changing up the file system? Sucks, I just have all my music/movies/photoshop/art stuff on my 500G drive and a tiny part of it devoted to Linux. Guess I'll have to change it up a bit. Thanks to everyone for the help regardless. :)

---

### Post by autocrosser on 2006-07-08
Let's see---

#1--You contacted the forum about your problem--that's NOT DUMB---

#2--I don't know if this will be much help, but I use external Firewire drives for my data storage & the internals to run the OS of choice--Allows the data to be portable & I can reset my drive set-up anyway I want.

#3--Welcome to UBUNTU!!!

---

