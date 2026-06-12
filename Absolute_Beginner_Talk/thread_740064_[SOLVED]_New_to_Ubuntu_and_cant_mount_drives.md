---
title: "[SOLVED] New to Ubuntu and cant mount drives"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-03-30
I mounted two of my partitions from windows after I finished installing Ubuntu.  I was accessing them just fine.  I tried to hook up my ipod, which has a harddrive that fails sometimes,  When i was transferring music all of a sudden my laptop froze and I couldnt do anything.  I had to restart by holding the power button, after that I have not been able to access either partition.  One of the partitions has a icon on the desktop, I have tried many different commands.  Now one partition says "You are not privileged to mount the volume 'Music'. and the others says "Unable to mount the volume." and when i click on details it says " fuse:mount failed:device or resource busy".  I get these messages every time I try mount these drives.  Please help me.  What should I do?

---

### Post by sancho panza on 2008-03-30
I dont know much about the error messages, but I would see if I can reboot into windows, check if I can access the drives ok from windows, then reboot back into linux and see if I can access them now.

---

### Post by dsauxier on 2008-03-30
If I understand correctly, you were booted to Windows when you had to kill the power, and now you're unable to mount those partitions in linux.

I think you need to boot to Windows one more time and let scandisk clean up the partitions.
(it should do so automatically on first boot after the hard shutdown).

If that doesn't work, It's also possible to do the same thing on linux, but I'm not sure what utility to use for FAT32 or NTFS (do you know which it is).

---

### Post by sirisaac87 on 2008-03-30
I was in linux when I had to hard reset, then I tried logging into windows shutting down properly then logging back into linux but I will had the same problem.  The partitions that I am trying to mount are both (nfts).

---

### Post by dsauxier on 2008-03-30
> **sirisaac87 said:**
> I was in linux when I had to hard reset, then I tried logging into windows shutting down properly then logging back into linux but I will had the same problem.  The partitions that I am trying to mount are both (nfts).

I've used fsck, but it does not support NTFS.
I did some searching and there is a package that you can install called ntfsprogs
(happily, it's in the officially supported repositories)
System->Administration->Synaptic Package Manager
Then search for ntsfprogs and install it.

I've never used this, but it provides a utility called ntfsfix

[INDENT]**DESCRIPTION**
       ntfsfix  is  a  utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS
       inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other way and it can’t be mounted.[/INDENT]

You need to find out which disk/partition are the ones you're interested in (the ones listed as ntfs).
It should be listed in the /etc/fstab file.  Here's an example : 
[INDENT]# /dev/sda7
UUID=714873b5-1506-448b-9f73-0d5bbeaef83c /home           ntfs     defaults        0       2
[/INDENT]
If /home was the partition I was interested, I know it's /dev/sda7 (the comment was put in there by the installer, so I'm assuming those comments have not been changed.  

Let's say you found the ntfs partition was /dev/sdg9 (you'll change the sdg9 to whatever you found from the /etc/fstab file - if you're unsure, then post here for more guidance before running this command)
Based on the descripion from the man[ual] page (man ntfsfix) I would run  
```
sudo ntfsfix /dev/sdg9
```
You'll actually do this on both ntfs partitions

Then boot to windows again, and let it run it's check.
If anyone reading this has any NTFS experience, please jump in with your commentary on this one.

---

### Post by sirisaac87 on 2008-03-31
I just wanted to say thanks for all the help with this problem, I dont know if there is something special you have to do to close a post or if you just leave it alone and it will eventually delete itself.  This issue is resolved

---

### Post by Miljet on 2008-03-31
Please post what you did to resolve the issue. It may be of help to others with similiar problems.

---

### Post by dsauxier on 2008-03-31
After that, you can click on "Thread Tools" and then "Mark this thread as solved"
That will leave the thread out here for the benefit of others, but mark it as solved so that people don't continue trying to troubleshoot it.

---

