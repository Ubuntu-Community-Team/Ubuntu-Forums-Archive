---
title: "Meddling with fstab"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by rzj on 2007-06-28
More dumb questions.... ](*,)

Since my initial install, I've added drives, added ntfs-3g (and run its config program a few times), repatitioned some of my drives and changed partitions from ntfs to fat32 and also to ext3. As a result I've had to get to grips with editing my fstab. This has generally worked OK, but I'm conscious that many of the original entries were by UUID and my own are just in /dev/... form. Which is OK, but not very robust if I swap drives around as I am prone to doing.

So how do I regenerate those UUID entries?

Also my "Places" list in Nautilus includes some of the drives but not all of them - how does that work?

And finally is there a mode in Nautilus (or an alternative file browser) that can give a view of drives that shows some combination of total size/used/free space?

Ray

---

### Post by moore.bryan on 2007-06-28
[I]the command
```
ls /dev/disk/by-uuid -lh
```will give you the uuid.
sorry i can't help you with nautilus... i don't use it.
the command 
```
df -h
``` will help with free space on disks...
[/I]

---

### Post by rzj on 2007-06-28
Thanks.

Had a quick look at the OpenBox site as a result of your sig. Am I right in inferring that it allows you to mix and match gnome and kde tools yet make them behave in a consistent way?

Ray

---

### Post by moore.bryan on 2007-06-28
*in a way, i guess you can say that.  it's considered a light-weight (in my opinion, the most light-weight) dm.  you can already use gnome tools in kde and vice-versa... openbox is just super light on resources.*

---

