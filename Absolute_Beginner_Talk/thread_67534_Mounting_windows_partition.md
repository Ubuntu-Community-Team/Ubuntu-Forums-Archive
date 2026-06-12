---
title: "Mounting windows partition"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by raincloudboy0 on 2005-09-20
Hey.

Been reading around this forum and in lots of other places, but still haven't found any answers to my questions. I'd greatly appreciate some help.

Basically, first of all, do I still have Windows XP? I installed yesterday from Windows XP. On typing sudo fdisk -l, I get this:

Disk /dev/hda: 81.9 GB, 81943142400 bytes
255 heads, 63 sectors/track, 9962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        9962    79770757+   5  Extended
/dev/hda5              32        9962    79770726   8e  Linux LVM

Does the "Extended" thing mean that I don't have Windows any more? What does it mean at all?

Assuming, however, that I still have Windows XP, I tried to mount the partition. I used the guide found here ([http://www.frankandjacq.com/ubuntuguide/5.04/#mountunmountntfs)](http://www.frankandjacq.com/ubuntuguide/5.04/#mountunmountntfs)), following the NTFS directions because I thought that since I have XP it would be NTFS, and got this:

wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I tried the same thing with the vfat option just in case; no more luck.

Help please? Thanks in advance.

---

### Post by sethmahoney on 2005-09-20
Based on the info you gave, it looks like you don't still have XP installed.

---

### Post by mlomker on 2005-09-20
The *extended* thing is just a hard disk option.  You can have multiple primary partitions on a drive or one primary and an extended parition with multiple "drive letters/partitions" in the same  extended partition.

I agree with Seth--you erased windows if you only have one drive.

---

### Post by raincloudboy0 on 2005-09-20
Okay, thank you.

Assuming that Windows is gone, then, how do I access all my files? I had music, documents, pictures, things like that. Are they gone too or am I just having issues getting to them?

---

### Post by mlomker on 2005-09-20
> 
Assuming that Windows is gone, then, how do I access all my files? I had music, documents, pictures, things like that. Are they gone too or am I just having issues getting to them?

We think you erased all of them...that's what we're saying.

---

### Post by raincloudboy0 on 2005-09-20
All right, thank you. 

Just one last question: in that case, how do I use the space that is now partitioned as "Extended"?

---

### Post by mlomker on 2005-09-20
That isn't an actual drive, even though Ubuntu gives it a partition number.  hda2 and hda5 are the same thing--a fairly small partition that is used for the swap file.

You can look at your disk space with the **df -h** command in a terminal.

---

### Post by raincloudboy0 on 2005-09-21
So I can access all parts of my drive from Ubuntu now, then?

Thanks for your time.

---

### Post by sethmahoney on 2005-09-23
Hey, sorry to hear you lost all your documents and stuff.  I know that can be a real pain.  Yeah, it looks like you're accessing your entire drive.  You might want to type

mount

in the terminal and post the output here.  Reason being, to help prevent document loss in the future I'm about to recommend (depending on the output of the 'mount' command) that you reinstall Ubuntu and place /home in its own partition (if you need instructions on how to do that, let us know - we'd be happy to help).  This helps to ensure that, if you ever have to reinstall Ubuntu (or another Linux distro, for that matter), your data wont be touched during the reinstallation process (you still have to be careful about it, but its not as dangerous).  If you have it set up that way you can completely wipe the other partitions and keep your documents (and even most of your settings) untouched.

Also, if you want XP back (this wont restore your documents, but will let you boot into Windows if you want), we can point you to some guides on how to install a dual-boot system that lets you choose when you start your computer whether to boot into Windows or Ubuntu.

---

