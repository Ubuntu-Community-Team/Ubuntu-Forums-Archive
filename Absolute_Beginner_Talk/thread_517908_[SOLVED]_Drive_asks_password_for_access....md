---
title: "[SOLVED] Drive asks password for access..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-08-05
When I try to access my 10 GB hard disk partition,Ubuntu asks for the password.The partition I'm talking about was a NTFS parttion which I reformatted to ext3 with Gparted Live CD.When the drive opens up it shows that it contains only a folder lost+found(In fact all the other drives also contain that particualr folder).Trying to set the permission to 'Read and Write' has been proved futile because it showed an error:"Sorry,could not change the permission  of.....GB hard drive".Would you please tell me how to deal with the problem.

Thanks in advance....

---

### Post by felicity on 2007-08-05
You might try changing the permissions with

```
sudo chmod -R a+rwx /path/to/drive
```

where /path/to/drive is the location of the drive you want changed.

The lost+found folder is on every ext3 formatted drive.

Below is information about the lost+found directory copied from a post by Moma:

Fsck -- File System Check.

In the rare cases of crash or malfunction of a harddrive the system vil automatically perform a filesystem check (fsck) at next boot. You can also perform fsck manually.

Fsck puts all corrupted (possibly damaged) and rescued files to "lost+found" directory. Each partition has its own lost+found.

Fsck has separate tools for each filesystem type; fsck.ext2, fsck.ext3, fsck.reiserfs, fsck.cramfs etc. You must unmount a partition before perfoming fsck.

Read:
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

Note: I believe that Ubuntu will run fsck each 30'th day or after 180'th boot or mount, which ever come first. Correct me if you know better ;-)

You can probably force a filesystem check at next boot by creating a "forcefsck" file in the root of partition.
Sample:
$ sudo touch /forcefsck
or
$ sudo touch /media/sdb1/forcefsck
----

shutdown -F is another way to force fsck at next reboot.
$ sudo shutdown -F -h now
And you'll see "Checking all filesystems" message in the boot screen when starting up.

Then check "lost+found" directory in each partition to see if any bad files was rescued.

---

### Post by chatterjee on 2007-08-07
The drive concerned is not mounted.Please say what should one do in this situation?

PS:Screenshot:

---

### Post by asleepfromtheday on 2007-08-07
can you post the line from your fstab?

---

### Post by chatterjee on 2007-08-07
Thank you.
I've just mounted the drive by right clicking and it's working fine now.

---

