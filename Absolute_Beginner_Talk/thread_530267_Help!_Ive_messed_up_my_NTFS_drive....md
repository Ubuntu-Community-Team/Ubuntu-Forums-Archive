---
title: "Help! Ive messed up my NTFS drive..."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by orange2k on 2007-08-20
I did a lot of downloading lately and I almost filled up my NTFS drive where Windows used to be (hehe), 
but though it wasn`t quite full yet, it got messed up. So I erased some 5 GB of data, but it still says "0 bytes available". The disk is still readable and I intend to copy the data to a removable HD and then format the disk to ext3 (or ext2? Im not sure....) and bring the data back.

What tools do I need? Something like gparted? Anything else I should know?

---

### Post by LaRoza on 2007-08-20
> **orange2k said:**
> I did a lot of downloading lately and I almost filled up my NTFS drive where Windows used to be (hehe), 
but though it wasn`t quite full yet, it got messed up. So I erased some 5 GB of data, but it still says "0 bytes available". The disk is still readable and I intend to copy the data to a removable HD and then format the disk to ext3 (or ext2? Im not sure....) and bring the data back.

What tools do I need? Something like gparted? Anything else I should know?

If you can get the data stored elsewhere by copying it as you said, you can use GParted to reformat the partition. If you are dual booting with Ubuntu, you might want to get the Windows entry out of grub.

I suggest using the Live CD, it is very useful.

---

### Post by ukripper on 2007-08-20
> **orange2k said:**
> I did a lot of downloading lately and I almost filled up my NTFS drive where Windows used to be (hehe), 
but though it wasn`t quite full yet, it got messed up. So I erased some 5 GB of data, but it still says "0 bytes available". The disk is still readable and I intend to copy the data to a removable HD and then format the disk to ext3 (or ext2? Im not sure....) and bring the data back.

What tools do I need? Something like gparted? Anything else I should know?

If you intend to backup the entire HDD try clonezilla and for the above purpose gparted should be enough and also Live Cd as suggested above

---

### Post by asmoore82 on 2007-08-20
If you deleted the files with the GUI they would be in a "Trash" can.

trash for external volumes is usually at the toplevel of that volume in a folder named ".Trash-*<yourusername>*"

you DO NOT want to use ext2.
ext2 is lightning fast compared to FAT/NTFS but it is a totally non-journaled system with
absolutely no protection against Power failures or force downs.
ext3 is right up there in speed but has journaling to protect data.
in fact the filesystems are identical except for journaling...
the cmdline to create an ext3 filesystem is 'mk[SIZE="2"]**e2**[/SIZE]fs -j' :p

---

### Post by orange2k on 2007-08-21
The drive is not working anymore...:(
It seems that somehow I messed up the MBR which was probably located on that drive. Now I just get the message "Boot failure" or something like that. I reinstalled Ubuntu on another drive, after Ive backed-up the working drive, but the NTFS drive is not recognized properly - I can see it as a second floppy drive with 2.7 GB space left, but no files are visible. Is there a way I could recover this drive myself or do I have to seek proffessional help from a specialized company that deals with this sort of stuff?

---

### Post by cbilljones on 2007-08-21
I would give a knoppix disc a try, very versatile at reading all file structures and giving you the access you require; quick to download from there torrent tracker

---

### Post by ukripper on 2007-08-21
> **cbilljones said:**
> I would give a knoppix disc a try, very versatile at reading all file structures and giving you the access you require; quick to download from there torrent tracker

Knoppix is very powerful and has tendency to startup quickly and have also got plenty of tools to analyse.

---

### Post by orange2k on 2007-08-21
I tried Knoppix, but it didnt help. I can see the drive, but cannot mount it. Are there some other tools that I might try?

---

### Post by ukripper on 2007-08-21
Your best bet is to copy your data over to external source or create a backup of ntfs partition and then format ntfs partition to ext3 using gparted from the LiveCD if you are using it for data only you can also format it to reiserfs for faster access( for stability i would recommend ext3).

---

### Post by orange2k on 2007-08-22
Nevermind, Ive tried Pmagic, Gparted - nothing works - the drive is not readable at all...
I disconnected the drive and plan to trash it. Ive asked for specialized help from a company that deals with this sort of stuff but they would charge for it more than the disk + the data thats on the disk is worth. So...:(

---

