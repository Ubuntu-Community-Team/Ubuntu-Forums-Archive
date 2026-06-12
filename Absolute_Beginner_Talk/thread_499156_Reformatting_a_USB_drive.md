---
title: "Reformatting a USB drive"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by gewitty on 2007-07-12
I have an external Seagate USB drive (identified as /dev/sda) that started out with several partitions under Windows XP. Now that I am running Ubuntu exclusively I need to clean up and reformat this drive. I have GParted, but some of the partitions are very screwed up and what I really need to do is reformat the whole drive and then start from scratch.

Can anyone tell me the best way to do this?

---

### Post by Inxsible on 2007-07-12
Well if you have GParted, that is all you need. First you need to unmount all the partitions.

If you are using the GParted on the LiveCD, you might want to start GParted and then unmount the sda partitions. For some reason, when i start up GParted in LiveCD, it mounts all the drives :(

So anyway, after unmounting, simply delete all the partitions that you want to delete and you should have a huge contiguous chunk of unallocated space. Create new partitions in it depending on how you want it and make sure to format it to which ever file system you want (EXT3 i suppose)

CAUTION: Make sure its the correct drive. Check this by checking the size of the drive thru commands like

```
df -h
```

---

### Post by sailor2001 on 2007-07-12
if you are going to reform anyhow and then rebuild......Just put in your install disk and select "entire disk"

---

### Post by Inxsible on 2007-07-12
> **sailor2001 said:**
> if you are going to reform anyhow and then rebuild......Just put in your install disk and select "entire disk"

I dont think the OP wants to install linux on this usb drive. he simply wants to format it in a native linux filesystem. He already has installed linux i believe.

---

### Post by gewitty on 2007-07-12
I got most of the existing partitions unmounted and deleted, but the freed space is not contiguous because there are a couple of items that appear to be locked in some way (see attached screenshot) and I can't find a way to remove these.

---

### Post by gewitty on 2007-07-12
I managed to get the two offending partitions unlocked and now have the full disk capacity formatted as a primary drive. Thanks for the help.

---

### Post by Inxsible on 2007-07-12
> **gewitty said:**
> I managed to get the two offending partitions unlocked and now have the full disk capacity formatted as a primary drive. Thanks for the help.

Glad you could work it out !!

---

