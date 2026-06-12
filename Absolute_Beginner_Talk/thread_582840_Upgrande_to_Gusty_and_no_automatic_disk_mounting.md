---
title: "Upgrande to Gusty and no automatic disk mounting"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Harvs on 2007-10-20
Hi

I've just upgraded to Gusty from Feisty which really smoothly. Just noticed one issue, which I haven't found an answer to yet....

In Feisty, I added lines to the fstab file to automatically mount to other partitions and another hard drive, which worked fine.

However, after the upgrade to Gusty, the mounting no longer works. But, in Nautilus it now lists the other partitions and hard drives under Places. Which is great. The only issue is that I have to double click and enter my password every time I boot Unbuntu to mount them.

Is there any way to automatically mount these??

Cheers
Harvs

---

### Post by Paqman on 2007-10-20
You'd need to add those lines back into your fstab. Gutsy has overwritten your changes.

---

### Post by Harvs on 2007-10-20
Hi Paqman

The lines are still in fstab, but they seam to no longer work...

```

/dev/hda1 /home/windows ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /home/files vfat iocharset=utf8,umask=000 0 0
/dev/hdd1 /home/back_up vfat iocharset=utf8,umask=000 0 0

```

---

### Post by Harvs on 2007-10-20
Ah, I've fixed it.

I had a look at
```

sudo nano fdisk -l

```
which told my the naming of the partitions and other hard drive has changed to what it was before.

So update fstab with the new names, and it's all working fine.

Phew...

---

### Post by asimon on 2007-10-20
Just a note regarding your NTFS entry. You may want to switch to the ntfs-3g driver which provides stable read/write access to ntfs. You need to install ntfs-3g and your fstab entry should look similar to something like

```
/dev/xyz /home/windows ntfs-3g defaults,locale=en_US.utf8 0 1
```

See more about the ntfs-3g driver in [MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions").

BTW, your problem is the reason why Ubuntu uses UUIDs for identifying partition by default. They stay the same whereas device names can change because of different reasons. See [UsingUUID]("https://help.ubuntu.com/community/UsingUUID").

---

### Post by Harvs on 2007-10-20
Cool, thanks. I'll take a look at those links...

---

### Post by Harvs on 2007-10-20
Installed ntfs-3g, so can write to my windows partition now, and changed the partition references to UUID, so shouldn't have this issue again.

Fantastic - thanks for your help asimon!

---

