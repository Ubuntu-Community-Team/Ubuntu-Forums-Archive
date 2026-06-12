---
title: "Problem getting  rw on usb mounted ext3 formated external hd."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by uglowp on 2007-10-19
I have a problem getting rw permissions on a usb mounted external hd.

Drive is 1 partition, formatted ext3.

HD mounts OK, on /media/hp_pmd, when it is plugged into the usb port

I used chown -R philip:user /media/hp_pmd , to change the user rights

ls -l shows philip and users as owners.

Yet I still can't  rw to the drive.

When I right click on the disk icon and click on properties and then permissions the owner is still root.

I don't get it?

Anyone know what I am doing wrong?

Thanks.

---

### Post by Arthur Archnix on 2007-10-19
Try this:
```
sudo chown -R philip:philip /media/hp_pmd
```

---

### Post by OttifantSir on 2007-10-28
This is my problem too.

Exactly. I have tried gksu nautilus, chown, chmod, tried mounting it manually with normal mount and pmount.

No matter what I do, the owner is still root, only one with RW-permissions, group is root with access, and others have nothing.

When I made a folder on my desktop and mounted the drive to that folder, I could get RW-permissions, as I didn't sudo mkdir that folder. But that seems to me to be an inefficient way of getting RW-permissions.

It won't automount either anymore.

This particular drive has been mounted and used in various ways: Directly connected to this laptop, connected to a server and accessed through SAMBA, formatted with FAT32 and NTFS earlier, now ext3. I have partitioned it to all of these filesystems using GParted on the laptop, and Norton Partition Magic in XP Pro SP2. I have accessed it through XP when formatted with ext3 using the Windows-utility for it. I have accessed and written to it through SAMBA when mounted and accessed in XP with FAT32, NTFS and ext3.

So, it seems really strange that when connecting and mounting it directly to a GNU/Linux system with ext3, I can't use it anymore when ext3 is a native GNU/Linux file system.

---

### Post by Arthur Archnix on 2007-10-28
To uglowp, if the suggestion worked perhaps you could mark the thread solved. If not, and you've found the solution perhaps you could post that as well.

To ottifantsir, you should start your own thread and be a little more specific about the errors that you are getting, and the commands you are trying.

Best,

---

