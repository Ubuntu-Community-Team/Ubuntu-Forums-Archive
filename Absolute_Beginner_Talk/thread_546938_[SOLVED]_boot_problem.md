---
title: "[SOLVED] boot problem"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by inter-m on 2007-09-09
Strange thing happens when I boot my laptop... it suddenly stops and prompts me to the command line telling me that apt-get is not installed... i tried to install it from there by typing 

```
apt-get install apt
```
and
```
aptitude install apt
```

as it asks but nothing happens... I then preform a Ctrl D which continues to the login page... and after i login I checked from the terminal and both apt-get plus aptitude are installed... Im totally confused here... :confused:

---

### Post by tcoffeep on 2007-09-09
Does it inform you that something happened in fsck-check? This happens every time fsck runs on my laptop...

---

### Post by inter-m on 2007-09-09
> **tcoffeep said:**
> Does it inform you that something happened in fsck-check? This happens every time fsck runs on my laptop...

yes it does...

---

### Post by st33med on 2007-09-09
Can you do this in the desktop:
```
sudo apt-get install amarok -s
```

Don't worry, this won't install anything on your computer if you add the '-s' at the end. Does it do anything?

---

### Post by inter-m on 2007-09-09
> **st33med said:**
> Can you do this in the desktop:
```
sudo apt-get install amarok -s
```

Don't worry, this won't install anything on your computer if you add the '-s' at the end. Does it do anything?

yeah it reacts as if it's installing... as i said both apt-get and aptitude are both installed when i lognin but the problem im having is when i boot...

---

### Post by st33med on 2007-09-09
Post the output from this:
```
dmesg
```

A temporary fix would be to download Bonager. This informs you how much time you have before a disk-check.
```
sudo apt-get install bonager
```

---

### Post by inter-m on 2007-09-09
i'll try what you suggested in a moment... but i have a question could this be due to the fact that I had made an adjustment to one of my partitions which i changed to a swap partition and  i didnt adjust the fstab... 

please check this string to have a better idea...
[http://ubuntuforums.org/showthread.php?p=3338659#post3338659]("http://ubuntuforums.org/showthread.php?p=3338659#post3338659")

---

### Post by st33med on 2007-09-09
try this:
```
sudo fdisk -l
```

Does it give any output?

---

### Post by Bothered on 2007-09-09
> **inter-m said:**
> i'll try what you suggested in a moment... but i have a question could this be due to the fact that I had made an adjustment to one of my partitions which i changed to a swap partition and  i didnt adjust the fstab... 

That could cause a problem, as the uuid of the partition may have changed. Try:

```
ls /dev/disk/by-uuid/
```

and paste the output here.

---

### Post by inter-m on 2007-09-09
this is what i got...

637f8d03-bea7-4eaa-9465-b17178880220  a3fa3aea-f48a-468a-9697-56289e6e50bf

---

### Post by Bothered on 2007-09-09
Looks like the uuid of the sda4 partition has changed. Try changing the line for sda4 in fstab to:

```
UUID=637f8d03-bea7-4eaa-9465-b17178880220 /media/sda4 ext3 defaults 0 2
```

and see if that helps.

EDIT: Also, you should add your swap partition to fstab as describer by scxtt, or your memory problems will come back.

---

### Post by inter-m on 2007-09-09
i tried what you said and it didnt work... so i deleted the sd4 entry from the fstab and guess what its working now... :guitar:
i really appreciate the help thanx...:)

---

### Post by tcoffeep on 2007-09-11
It may be solved...

but, here's a way to delete fsck...It saves me the trouble of all the problems:

> The e2fsck will regularly force a check of a filesystem even if the filesystem is marked clean. By default, this happens on every twenty mounts or 180 days, whichever comes first.

The ext3 filesystem does this as well, which can be annoying if you have a very large filesystem and a short downtime window. Therefore, it’s a good idea to disable this feature on large volumes. Keep in mind that you should still run fsck occasionally, by disabling the automatic checks, you get to Decide when, not the system.

Use the command:

```
sudo tune2fs -i 0 /dev/hda1
```

It was hda1 in my case

---

