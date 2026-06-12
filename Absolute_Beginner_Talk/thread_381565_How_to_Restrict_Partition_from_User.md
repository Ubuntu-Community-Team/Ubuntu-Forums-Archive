---
title: "How to Restrict Partition from User"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-03-11
I want to restrict one partition from other users.
Now if I unmount from desktop, can I mount it easily when I want ?
Is there any other way I can do it ?
It is an EXT3 partition.

---

### Post by Ocxic on 2007-03-11
in your fstab set the UID and or GID your your  user and only you will bae able to see/use that partiton:

ex
```

# /dev/md1
UUID=2b754260-f592-4ce0-8cce-1ffcf53af08d /home           xfs     defaults,uid=1000,gid=1000        0       2

```

you can find your user id and ground id in the user/group app under system->administration

---

### Post by dptxp on 2007-03-11
Do I edit the line or add a new line in fstab ? And do I go to fstab using the Terminal ?

---

### Post by wj32 on 2007-03-11
> **dptxp said:**
> Do I edit the line or add a new line in fstab ? And do I go to fstab using the Terminal ?

```
sudo gedit /etc/fstab
```

---

### Post by steve.horsley on 2007-03-11
> **dptxp said:**
> Do I edit the line or add a new line in fstab ? And do I go to fstab using the Terminal ?

Use Alt-F2 to get a small command prompt, and enter the command **gksu gedit /etc/fstab**.
If there is already a line for that partition, edit that line rather than make a second line. My preference would be to duplicate the existing line and comment one copy out by putting a # at the front, then edit the other copy. 

After saving the changes, you need to umount the partition and then mount it again:
sudo umount whatever
sudo mount whatever

---

