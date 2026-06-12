---
title: "Defining mount points during install"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-30
Hi,

I want to dualboot XP with Ubuntu and have set partitions on my 60Gb disk as follow:

Primary partitions:
-------------------
hda1: XP (NTFS, 10Gb)
hda2: Ubuntu (ext3, 10Gb)

Extended partition (hda3):
-------------------------
hda5: /tmp (FAT32, 4Gb)
hda6: linux-swap (1Gb)
hda7: /home (Ext3, 32Gb, accessed from XP with Paragon Mount Everything 3)

XP is already installed on hda1 and all other partition have been formated with the specified formats with GParted. Now I come to the "Prepare mount points" dialog in the installation process (step 5/6). According to the above settings I set the mount points as follow:

hda1: /media/hda1
hda2: /
hda5: /tmp (manually written)
hda6: swap
hda7: /home

I press "Forward" button and I get the following message which prevents me to go on with the install:

"FAT and NTFS filesystems may not be used on filesystems used by the system (/, /boot, /home, /usr, /var, etc). It is usually best to mount them somewhere under media."

So my questions are:

1) Is this error caused by me having manually written /tmp to mount the /tmp filesystem on hda5 (hda5 is FAT32)?

2) The message says that even the /home filesystem may not be used on a FAT partition. I don't understand that since most dualboot guides recommend to share /home with XP on a FAT32 partition... I will use an Ext3 partition for /home but why does the install process tells that /home cannot be mounted on a FAT system???

3) Rather than creating a separate partition for /home (which would contain personal documents and application settings), I'd prefer leave /home with / but have a separate partition for /data (only my documents). How can I do that? Is this possible to do it from the install process??

4) The mount point of the XP partition (hda1) is /media/hda1. Will this be the name of this partition under linux?? I'd prefer to label it "WINXP" so should I write "/winxp" as the mount point of hda1 or should I leave it alone for now?? Are mount points and labels 2 different things??

Many thanks and sorry for the long post and these noobs questions!

---

### Post by Bachstelze on 2006-11-30
1) As the message says, it's a bad idea to use non-Linux filesystems on system folders. Is there a particular reason why you want it as FAT, or why you want it on a separate partition at all ?

2) Because most people like their /home private and FAT can't handle file permissions.

3) What I'd do if I were you - and what I've done on my systems, too ;) - is create a big data partitions to store all kinds of stuff and create a subdir on it to store user's home folders. Like this, you can have /data/homes/user_ubuntu, /data/homes/user_slackware, /data/homes/user_freebsd, whatever you want ! (Then, try do do just that in Windows for a good laugh :p)

4) It's usually best to have it in /media, you could mount it on /media/winxp.

---

### Post by rbprogrammer on 2006-11-30
so then why dont you just mount your [/tmp] on a partition that is ext3?  is there a particular reason why you want it as fat32?

---

### Post by taurus on 2006-11-30
You cannot install Linux on fat32 filesystem!!!  It has to be ext2, ext3, reiserfs, etc. but not fat32 or ntfs...  Personally, I recommend you use ext3 for /, /tmp, and /home.

---

### Post by Bachstelze on 2006-11-30
Personnaly, I recommend Reiser, though you probably won't notice any difference :p Also, use ext2 for data storage, you don't need journaling on them anyway.

---

### Post by kilou on 2006-11-30
Thanks for your replies!

I wanted to create a separate partition for temporary files of both Ubuntu and XP. I like to do that to prevent fragmenting on other partitions and to keep them clear of temporary files. I planned to put the following on this temp partition:
- XP users and system temporary data
- XP pagefile.sys (virtual memory)
- Ubuntu /tmp filesystem

The reason I wanted it to be FAT32 is that:
1) it must be accessible to both Ubuntu and XP
2) I don't want it to be NTFS and have to use the "experimental" NTFS driver for linux
3) I don't want it to be Ext3 because the XP pagefile will be on that partition and Paragon Mount Everything software (used to access Ext3 partitions from Windows) does not recommend to put XP system files such as the pagefile on a Ext3 volume.

The big thing I don't understand is that most guides recommend to put /home on a separate FAT32 partition to acces it from linux and XP. How then can they do that if it is not possible to put /home or an other system "folder" on a FAT volume?? FAT cannot handle file permissions but as these guides say although it is a drawback /home can be put on a FAT volume. In my situation it seems I simply cannot put any system folder on a FAT volume.

Arrgh I think I'll have to rethink my partitioning strategy all over again ](*,)

---

### Post by taurus on 2006-11-30
If you want to share files between Windows and Ubuntu, format it as fat32 and mount it somewhere like /media/share...

---

### Post by kilou on 2006-11-30
Actually sharing documents is not a problem since I'll place /home on a ext3 partition and access it from XP with a special driver. The problem I have is with /tmp that cannot be mounted on a FAT32 volume. I want to share /tmp with windows to put XP temp and pagefile on it too but cannot use Ext3 here since this will slowdown the pagefile.

The question I had is why do some people seem to be able to mount /home on a separate FAT32 partition while I'm not able to do the same with /tmp? Both /tmp and /home are system "folders" and according to the error message I got they both may not be mounted on FAT32 volumes (not only /tmp).

---

### Post by Bachstelze on 2006-11-30
Normally, it is possible to do it, curse those "desktop" CDs that won't let you do anything unusual and get an "alternate" :p

---

### Post by kilou on 2006-11-30
Might be a solution: if I can share the swap space between XP and Ubuntu, the XP pagefile would have its own partition under when XP is booted. Therefore I could mount /tmp on a ext3 partition and share it with XP temporary folders through Ext2IFS or similar.

See my other thread: [http://www.ubuntuforums.org/showthread.php?p=1827098#post1827098](http://www.ubuntuforums.org/showthread.php?p=1827098#post1827098)

---

