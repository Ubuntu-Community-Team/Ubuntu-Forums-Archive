---
title: "slave drive installation"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by guddr on 2007-06-26
**I am a new user to 7.04 and I was curious as to the best way to add a slave drive for storage on my system.  It is formatted etc3. I know the hardware installation side but I want to be sure of permissions and being able to see it under my Home folder.  I would appreciate any suggestions. **

---

### Post by Yoooder on 2007-06-26
Well, if you are as far as having the device installed and formatted then the only thing you'll need to do is mount it.

You can manually mount the drive via command line, but it's much more convienient to have the system do it for you @ boot.  So to achive this you'll want to edit your /etc/fstab file.

Firstly:  Make a backup of the existing fstab, just in case
> sudo cp /etc/fstab /etc/fstab~

Then open up your fstab with your editor of choice
> sudo nano -w /etc/fstab

Go to the end of the file/list and begin a new entry.  The format is:
> [device] [mount point] [filesystem] [options] [dump options] [fsck options]

So a good default entry for your drive will be (fill in the [device] with your drive)
> /dev/[device] /mnt/[device] ext3 user 0 0

This will mount your drive to a folder like /dev/sdb1, and the "user" option will allow your user to mount/unmount it (instead of requiring root to do so).

Save your fstab changes and close the text editor.  Now try mounting the drive (the fstab entry just allows it to be mounted automatically at boot)
> mount /dev/[device]

Once the drive is mounted you should be able to change the ownership to your user:
> sudo chown [youruser].[yourgroup] /mnt/[device]

yourgroup should be the same as youruser, so for me it would be "chown yoooder.yoooder /dev/sdb1"

At this point you can add a symbolic link from your home folder to the mounted drive.  You could also mount the drive directly within your home folder, which would work fine--it's just a bit less standard.

Adding the symlink:
> ln -s /home/[youruser]/ /mnt/[device]

---

### Post by Yoooder on 2007-06-26
*removed, double posted*

---

### Post by guddr on 2007-06-26
Thank you, I appreciate your help.

---

