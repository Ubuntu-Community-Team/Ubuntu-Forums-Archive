---
title: "External hard drive issue"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by kolonel on 2007-09-07
Gday all, 

Long time reader, first time poster.

I have a 320GB hard drive that i originally had on my Windows XP system.  

I now run Ubuntu 7, and although i can read from the drive, i cannot transfer files to it.

/dev/sdb1 on /media/Backup type ntfs (rw,nosuid,nodev,umask=222,utf8)

is what it reads when i type in "mount"

Any help would be appreciated.

Regards
kolonel

---

### Post by overdrank on 2007-09-07
> **kolonel said:**
> Gday all, 

Long time reader, first time poster.

I have a 320GB hard drive that i originally had on my Windows XP system.  

I now run Ubuntu 7, and although i can read from the drive, i cannot transfer files to it.

/dev/sdb1 on /media/Backup type ntfs (rw,nosuid,nodev,umask=222,utf8)

is what it reads when i type in "mount"

Any help would be appreciated.

Regards
kolonel

HI and welcome, have you installed ntfs-config  and ntfs-3g? You can download them in synaptic manager, just search for ntfs. Hope this helps good luck! :popcorn:

---

### Post by Ek0nomik on 2007-09-08
Your hard drive is formatted as NTFS.  Ubuntu can't natively write to this filesystem, but as someone has already stated, you can install NTFS-3G.

You could also backup your data and reformat to a filesystem that Ubuntu will be able to read and write to natively.  FAT32 of EXT3 are the most popular.

If that isn't an option, you can install NTFS-3G.

```
sudo apt-get install ntfs-3g
```

---

### Post by kolonel on 2007-09-08
Hmmm, now the drive has disappeared from the desktop

kolonel

---

### Post by expatCM on 2007-09-08
If you WERE using Windows and are now NO LONGER using Windows you do not need to have the drive formatted to NTFS.  It may be a good time to change the file format to ext3.  

Please note that any data on the drive will be lost in making the change and backing up the data first may be a good strategy.  But you back up your data already .... ?   :)

---

### Post by kolonel on 2007-09-08
Didnt want to format drive, as i have information on there that i need to keep, and it wont fir on the laptop C:

I need to be able to write to the external, so i can dump the info from current drive to external drive.

Regards
kolonel

---

### Post by endre on 2007-09-09
I am in the same situation - I intended to use my external drive to back-up data from both my Windows and my Ubuntu partition, but this is messing up everything for me.

I have a seagate 500Gb external harddrive, formatted to NFTS, and installing the nfts.3g and config packages makes no difference!

---

### Post by expatCM on 2007-09-09
I also have 500GB external Seagate drives.   During a transition phase I have them formatted to FAT32 and they work without any issue.  In the next few weeks I will convert these drives to ext3 .. the only challenge is working out how to do this without loss of data

---

### Post by Harpoon on 2007-09-09
Installing ntfs-config is a great idea.  It has solved all of my external drive issues.  However, having the utility installed will do you absolutely no good until you open a terminal and enter the command "sudo ntfs-config"  The gui really is self explanatory.  I guess it is easy to assume that prople who ask questions simply "know" that some programs work on install, and others need to be explicity run by the user.

I hope this helps solve the "doesn't work for me" problems.

---

