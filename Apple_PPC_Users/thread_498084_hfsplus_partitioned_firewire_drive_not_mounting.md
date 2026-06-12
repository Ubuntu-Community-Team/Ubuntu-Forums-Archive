---
title: "hfsplus partitioned firewire drive not mounting"
date: 2007-07-10
forum: Apple PPC Users
---

### Post by tablebreaker on 2007-07-10
hey all-
i have 2 external firewire drive bays that both have 2 drives in them, for a total of 4 drives. all four drives mount in OS X automatically, but only 2 of them mount automatically in ubuntu, and they are both in the same case. what's the deal?

thanks!

---

### Post by pxwpxw on 2007-07-11
Could you post text from the file  /etc/fstab
and output from
```

 sudo mac-fdisk -l
### and from
 ls -l /dev/sd*

```
Should be enough to give a clue to the problem (assuming you had both firewire bays powered on before restarting).

---

### Post by tablebreaker on 2007-07-13
they actually all mounted when the boxes were powered on before plugging in, but I don't have rights to write files to them... how do I do this?
also, I can't write to my OS X paritition... how do I change this in fstab?

thanks!

---

### Post by pxwpxw on 2007-07-14
Three things you need do to write to mac hfs+ system from ubuntu.

In MacosX:

Disable journalling for the partition, and give "others" read/write permission for the folder you want to share (create one in the root of your macosx partition)

In MacosX terminal.app
```

 diskutil disableJpurnal /

```

Getinfo for the shared folder and in the permission details make it read+write for others

In ubuntu:
 use chmod to give the necessary write permissions for the mounting directory (on which the external partitions are auto mounted as listed in fstab, or manually mounted).

There are some previous discussion threads about writing to macosx hfs+ from ubuntu in the forum.

---

