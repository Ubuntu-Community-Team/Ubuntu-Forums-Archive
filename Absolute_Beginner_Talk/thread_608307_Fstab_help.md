---
title: "Fstab help"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by ~chinook~ on 2007-11-09
I needed to reinstall Ubuntu, so I made a separate partition to put my /home on. It is now on sda1. I then reinstalled Ubuntu on the other partition. Now, I tried to make fstab entry to use the sda1 as /home but get an error saying there is no home directory. The entry I made is as follows:

/dev/sda1 /home ext3 nodev,nosuid 0 2

Which is directly out of a guide. Any help would be appreciated. Thankfully I made a backup and just copied over the old fstab.

---

### Post by dwhitney67 on 2007-11-10
Ubuntu has it's own way to do things, but here's how it is done on a typical Linux distro:

[FONT="Courier New"]/dev/hda3       /home           ext3            rw              0       2[/FONT]

In your case, replace hda3 with sda1.

P.S.  Normally sda1 is your root (/) partition, then sda2 is either the next partition (/home) _or_ your swap partition.  Make sure your "ducks are in a row" before you make any assumptions about the partitions.  On my system, the "a1" is the root partition, "a2" is the swap, and "a3" is the /home partition.

---

### Post by ruibernardo on 2007-11-10
Ubuntu uses UUIDs in /etc/fstab since Edgy. You have to add the UUID of the partition in /etc/fstab instead of the device.

To find which is the UUID of a partition, mount it and run "blkid" or look [this post]("http://ubuntuforums.org/showthread.php?t=427612") for another way to get the UUIDs of a partition. 

Then update /etc/fstab with the UUID instead of /dev/sda1. For example, based on my fstab:
```
# /dev/hdc1
UUID=96f5d37a-7c14-4876-b83c-1fad4a8e7b45 /home           ext3     defaults         0       2
```

---

### Post by Jose Catre-Vandis on 2007-11-10
> **epimeteo said:**
> Ubuntu uses UUIDs in /etc/fstab since Edgy. You have to add the UUID of the partition in /etc/fstab instead of the device.

This isn't necessarily required. referring to devices in fstab (e.g. /dev/hda1) instead of a UUID is just fine

---

### Post by viking777 on 2007-11-10
I would go so far as to say that it is even preferable. Every time I install a new kernel in Ubuntu it replaces my devices reference with a uuid one and every time I go through fstab and replace the uuid's with device references.

Why?

Because all the uuid references are wrong - every time, and if I try to boot the pc with fstab in that state I get nothing.

Don't ask me why they are wrong because I haven't got a clue, I just know that they are.

---

