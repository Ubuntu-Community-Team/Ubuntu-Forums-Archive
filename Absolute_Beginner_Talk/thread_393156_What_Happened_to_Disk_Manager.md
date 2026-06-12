---
title: "What Happened to Disk Manager?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2007-03-25
There use to be a really useful tool located at System>Administration>Disks in Dapper but ever since Edgy I have not been able to find the disk manager.  Not only have I not been able to find it, I can't find another graphical tool for mounting partitions.  Whatever happened to the disk manager?

---

### Post by schwascore on 2007-03-25
I don't know what happened to the Disk Manager, but here is a simple replacement:

```
sudo apt-get install gparted
```

This installs the GNOME partition manager under the System --> Administration menu.

---

### Post by fatsheep on 2007-03-25
> **schwascore said:**
> I don't know what happened to the Disk Manager, but here is a simple replacement:

```
sudo apt-get install gparted
```

This installs the GNOME partition manager under the System --> Administration menu.

I have GPARTED installed.  What I wanted was a graphical tool to mount disks, not a partition editor.

---

### Post by Patrick K on 2007-03-25
You can mount and unmount partitions (disk) with gparted.

---

### Post by 23meg on 2007-03-25
[http://www.ubuntuforums.org/showthread.php?t=317742](http://www.ubuntuforums.org/showthread.php?t=317742)

---

### Post by fatsheep on 2007-03-25
> **23meg said:**
> [http://www.ubuntuforums.org/showthread.php?t=317742](http://www.ubuntuforums.org/showthread.php?t=317742)

Thanks for the link.  I still can't believe they removed Disks Manager.  This alternative program sucks in comparison.

---

### Post by 23meg on 2007-03-25
It's not possible to ship something as a default (or more precisely, in the Main component) when it's dropped by the upstream author and there's no guarantee of being able to provide support.

---

