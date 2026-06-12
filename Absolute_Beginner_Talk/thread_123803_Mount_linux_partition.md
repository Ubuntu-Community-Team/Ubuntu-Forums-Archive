---
title: "Mount linux partition?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by SilverTab on 2006-01-31
If I have 2 distributions on my HD, Suse and Kubuntu, is it possible to mount the  partition where kubuntu is installed in suze (or vice versa) to access the documents/files that are on it?  (I dont want to use the programs on the other partition, just access things like mp3, images etc)

---

### Post by aysiu on 2006-01-31
Yes, just ```
sudo mkdir /linux_distro
sudo mount -t ext3 /dev/hda1 /linux_distro
```

This assumes the other Linux distro is on /dev/hda1 and is Ext3 (not Reiserfs).

---

### Post by SilverTab on 2006-01-31
Ok excellent thanks! :)

second question: Im about to install the second distribution; can I use the same swap partition for both distribution?? or do I need 2 swap partitions!???

---

### Post by morphodone on 2006-01-31
[QUOTE=SilverTab]Ok excellent thanks! :)

second question: Im about to install the second distribution; can I use the same swap partition for both distribution?? or do I need 2 swap partitions!???[/QUOTE]

often times when installing another distro, it will automatically detect your swap parition...

so far i have had no problems sharing a swap parition between distros

---

### Post by SilverTab on 2006-01-31
exactly what I wanted to know! :)

thanks! I guess I will give it a try!

---

