---
title: "Need to recover some files..."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by firedraco on 2007-06-10
I have just updated to feisty, during the updating something went terrible wrong and I am not able to login anymore (it says that my preferences are used by another user). I thought that it would be easier just to backup my files in the home directory and do a fresh install into the machine. I installed an Internal Hard Drive to do the backup but the hard drive is being mounted as read-only. I am not able to copy/move the files out of my HOME folder ... Please help...

---

### Post by drowner on 2007-06-10
Hmm.

can you show us

sudo fdisk -l

and

cat /etc/fstab

---

### Post by KIAaze on 2007-06-10
Can't you even copy the files using "sudo cp"?

A better solution of course would be to mount the drive as read/write (assuming it's not NTFS of course):
Try:
```
sudo mount -w /dev/hdax /mnt/dir
```

Where "hdax" is the partition from the drive that you want to mount and "dir" is the directory where you want to mount it.
(I'm not sure it will work since "-w" is the default option already, but who knows...)

Also, do you mount the secondary HD automatically or manually?
If automatically, please post the /etc/fstab file to see.
If manually, well, how you mounted it.

---

### Post by ugm6hr on 2007-06-10
The easiest way to recover data  is to boot from a LiveCD (Ubuntu will do - but Puppy and others are faster).

LiveCDs generally log you in as root, so there should be no issues with accessing drives.

Only problem would be if the second drive is NTFS.

---

### Post by sandwitch on 2007-06-10
most logicall explanation is that your user has different uid and guid you can correct this with chown en chgrp
A drive that gets mounted read only is maybe a NTFS drive or needs an fsck

good luck!

---

### Post by firedraco on 2007-06-10
Thanks for the information! I was not aware that there were some issues with NTFS partitions (it is the same under MacOS X), good news is that the second hard drive that I installed had a FAT partition =)  (I have not seen it before )

I did the sugested

cp /home/* media/disk -r (which worked great!!, although I added the -v to see what was going on)... This is a pretty good comunity, I think this is way ubuntu is gaining ground within the Linux distros!!)

Thanks a lot...

Now is time to format and install the feisty!!!

PD: BTW I have read some other posts with people that had this problem (can not login after updating to fesity) is there any bug or what is the deal (my mom did the update using the software update utility, she did not download the LiveCD...)

---

