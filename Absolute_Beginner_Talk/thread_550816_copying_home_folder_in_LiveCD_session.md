---
title: "copying home folder in LiveCD session"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-09-14
Grub is having problems. I want to copy /home to a 2nd harddrive (both drives are Fesity). I have to run LiveCD session to get an OS. During LiveCD I can't use the Gnome File Manager to copy the folder from drive to drive. Is there a way to do this in the GUI? If there is no way in GUI, then how in command line. Yes, I mounted both drives.

---

### Post by mxg01 on 2007-09-14
From the command line you can try this:

cd home
sudo find . -depth -print0 | sudo cpio -–null -–sparse –-preserve-modification-time -pvd /mnt/newhome

That might be overkill from a live CD but that's what I used to copy my /home to a new partition without a problem. /mnt/newhome is the place for it to end up.

On the cpio command null, sparse and preserve are prefixed with double - signs. I suspect this will display them as one long line.

---

### Post by Mark_in_Hollywood on 2007-09-14
I'm still unsure as to what to do. I have two hard drives. Both formated with Feisty. the PriMaster "boot" drive has a folder /mark  I want to copy that to the second drive's /home/mark/Desktop/40Gig

where 40Gig is a folder sitting on the (2nd) drives Desktop.

From the LiveCD session, the two hard disks are:

/media/disk

and 

/media/disk-1


"disk" being the PriMaster and "disk-1" being PriSlave

I tried 

sudo cp /media/disk/home /media/disk-1/home/mark/Desktop 

no workie!

---

### Post by SOULRiDER on 2007-09-14
What errors are you getting? Press alt + f2 and run nautilus as root:
```
gksu nautilus
```
Try to copy the files using Nautilus, see if you have any issues.

---

### Post by Mark_in_Hollywood on 2007-09-14
This is a LiveCD session. Following your ideas, I saw the file manager window but no access to either of the two hard drives. I have no idea of what to do about this, but don't see an "error message". Anything else?

---

### Post by SOULRiDER on 2007-09-14
You have to mount the two drives first. Browse witht hat Nautilus Window to where they were mounted and copy the files over.

---

### Post by Mark_in_Hollywood on 2007-09-14
I have switched the Pri. Master and Slave to make A where B was and B where A was. 

I now have a bootable OS. I will try to copy the /home from the Pri-Slave. 

Thanks, community.

---

