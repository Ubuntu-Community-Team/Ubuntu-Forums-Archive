---
title: "Help ipod problem"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by adewale on 2006-12-08
please help me my brother just brought an ipod and needs music on it windows couldn't open the ipod. i inserted my kubuntu live cd and it mounted and when i try to open it, it says could not mount device and says its in fstab. also how can i view and copy files from an ntfs hard disk

---

### Post by deadgobby on 2006-12-08
Have you check Ubie Wiki site??
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=IPOD&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=IPOD&titlesearch=Titles)

Gobby

---

### Post by adewale on 2006-12-08
that link isn't helping at all. and how can i mount ntfs partition i just want to copy files thats all

---

### Post by SyvanX on 2006-12-08
If the NTFS partition is on the same hard drive, ubuntu should mount it automatically, then you can copy files from that partition to your Ubuntu partition.  

```
mount -t ntfs "*device name*" "*mount point directory*"
```

read up on mount, it should help you get familiar with the command.

```
man mount
```

---

### Post by adewale on 2006-12-08
thanks but still don't have a work around the ipod yet i don't have an internet connection over the (k)ubuntu i wonder why it says the ipod isn't in fstab?

---

### Post by scc4fun on 2006-12-08
> **adewale said:**
> thanks but still don't have a work around the ipod yet i don't have an internet connection over the (k)ubuntu i wonder why it says the ipod isn't in fstab?
If the iPod is brand new then the hard drive/memory of the iPod needs to be formatted. It is formatted the first time it is used. If you use it the first time on a Windows computer it'll be formatted as FAT32 (I think) or NTFS. You can use a utility to format the hard drive of the iPod to FAT32 so that you can easily copy music to it from Linux or Windows.

See [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

