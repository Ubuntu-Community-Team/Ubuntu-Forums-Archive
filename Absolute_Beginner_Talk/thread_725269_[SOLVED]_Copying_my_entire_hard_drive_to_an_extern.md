---
title: "[SOLVED] Copying my entire hard drive to an external hard drive"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-03-15
Hi, I'm trying to copy my entire internal hard drive ([http://ubuntuforums.org/showthread.php?t=725061](http://ubuntuforums.org/showthread.php?t=725061)) and save it to an external hard drive in case my system becomes corrupted/lost/deleted and I can just restore it.  However, I've been getting stuck.  I've tried making an image (and even compressing it) but as my hard drive has 60% usage it stops at 100% and I can't go any further.  Consequently, I've had to delete the backup file as it causes my 7.10 to freeze.  Can you help, please?

---

### Post by scragar on 2008-03-15
you could try:
```
dd if=/dev/**FROM** of=/**TO**
```where **FROM** is the partition you want to back up, and **TO** is where to save the info(eg: /media/disk/file.iso).

Can't say it'll work for definate though

---

### Post by freebios on 2008-03-15
you could also just partimage, run the live cd and install partimage and clone your drive!  hope it helps.

---

### Post by ruy_lopez on 2008-03-15
Use "tar"

The "tar" way:
```

sudo tar -cf - -C / . --exclude="mountpoint" | tar -xvpf - -C /path/to/mountpoint

```

This copies everything, but the drive you are copying into. Pay close attention to the command.

When you mount your drive, give the "mountpoint" a difficult name, so that "--exclude" doesn't inadvertently exclude real files.

EDIT: if you are going to use "dd", install "dcfldd" and use it instead. "dcfldd" takes the same arguments as "dd", but prints a constantly updating progress report.

---

### Post by Berean on 2008-03-15
Nope, doesn't work!  But thanks. (in response to dd, but I'll try the other suggestions).

---

### Post by Berean on 2008-03-15
ruy_lopez, something is definitely happening!  I suspect this will take some time, am I correct?  Also, how would I go about reinstalling these files should my system become corrupted/lost/deleted etc?

---

### Post by ruy_lopez on 2008-03-15
> **Berean said:**
> ruy_lopez, something is definitely happening!  I suspect this will take some time, am I correct?  Also, how would I go about reinstalling these files should my system become corrupted/lost/deleted etc?

It always takes a lot of time to backup everything. Once you have the backup, you can use something like "rsync" to do incremental backups. You can tell "rsync" to update only files that have changed etc.

Restoring your system is a little more involved. I usually do a fresh install of the operating system, set up the same user accounts as before, then replace the /home folder with the one that's backed up.

Once you have the home folder restored, almost everything is the same as before. You can then selectively restore the things you need. You are better reinstalling software from repositories than from the backup. If you had software configured a certain way, you can always restore the old config files.

The only other method I know is using "dd". But with "dd" you can only restore a drive that's identical to the old one. If the drives are different sizes, you need to mount the "dd" image using a loopback interface, and copy the files by hand.

Partimage can backup a partition. But after failure, if your new drive is a different size, you'll end up with a restore partition that's smaller. And I'm not sure if Partimage can do incremental backups. Plus the partition has to be unmounted. So you need to boot into a LiveCD (the last time I tried, the LiveCD didn't include Partimage. I had to make my own LiveCD).

---

### Post by Berean on 2008-03-15
ruy_lopez, thanks so much for your help.  I have now managed to copy everything of importance and will do as you advise if my system becomes corrupted: As you've written, I can always do a fresh install and then copy my config and personal files.  Once again, many thanks and enjoy your supper!  Regards.

---

