---
title: "Viewing hard drives as one"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by uservhy56 on 2005-09-21
Hello,

I have a file server with two 250gb hard drives. I want the people using the fileserver to be able to access them transparently through samba. I have samba set up, working etc. Volume shared is /home/test on disk 1. I would like this one folder to be able to expand into the second hard drive. Is it an LVM that I need or what is the best solution.


Also, how can I see what disks Ubuntu sees through the commandline?


Thanks.

---

### Post by Wolki on 2005-09-21
[QUOTE=uservhy56]
Also, how can I see what disks Ubuntu sees through the commandline?
[/QUOTE]

"sudo fdisk -l" will show all the partitions available, "df" will show all the mounted partitions and how much free space they have.

Not sure about your main question. Would it be sufficient to have the second partition as a directory in the first one? In that case, just create the new directory and edit your fstab so that the partition mounts there.

---

### Post by mlomker on 2005-09-21
You can use LVM to create a software RAID (such as RAID0 to span the drive) but that's a bit complicated if it isn't necessary.  You could just link one drive into another.

For example, /home/test would have the diskspace from the first drive and /home/test/folder would have the disk space of the second drive.

If you give me the output of **fdisk -l** and **mount** then it should be just a matter of creating a simple symbolic link.

```

ln -s /mnt/hda2 /home/test/foldername

```

---

