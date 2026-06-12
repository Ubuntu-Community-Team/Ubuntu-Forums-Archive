---
title: "[sdc] Assuming drive cache: write thru"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-01-17
I get this message continuously repeated:

[sdc] Assuming drive cache: write thru

This occurs on bootup and I never get into the GUI.  
I can log in at the command prompt but this message repeats about every 5 seconds.


Anyone have a solution?

Carl

---

### Post by cwmoser on 2008-01-17
Well, I recovered from the  ....

Kernel Panic - not syncing : VFS : Unable to mount root fs 

[sdc] Assuming drive cache: write thru

... errors.

Not sure if all the following was necessary but this is what I did:

- edited the Grub Menu removing the keycodes for the partition and replaced with root=/dev/sdb3

- rebooted and at progress bar, pressed Alt + F3 to drop to command prompt.
  installed gdm:  sudo apt-get install gdm
  entered:  startx

- reinstalled gnome, compiz.


Now I have my Ubuntu back to life again.

Carl

---

### Post by Ux64 on 2008-01-21
Yeah, it would very nice to know what causes this problem.

In my case it also lead to readonly volume, and data corruption. Chipset is IP35, do you happen to have same chipset?

And I won't use my computer before I know what causes this problem. I hate systems which corrupt data over and over again.

Problems with that chipset: [http://georgia.ubuntuforums.org/showthread.php?t=637721&page=2](http://georgia.ubuntuforums.org/showthread.php?t=637721&page=2)

fstab
```

UUID=1466f0a6-960d-4c85-9def-f2f0342b16c3 /               ext3    defaults,noatime,data=journal,errors=remount-ro 0       1
# /dev/sda5
UUID=09898500-dc53-45ff-80d2-6979c4eeb964 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,iocharset=utf8    0       0

```

---

### Post by cwmoser on 2008-01-21
Mine turned out to *not* being a hardware issue.  Instead, it was corrupted X configuration.

Basically, I booted to the command prompt and reloaded the GUI.  I think it was like this:

sudo apt-get install gdm

then, entered startx to start up X windows.


Carl

---

### Post by Ux64 on 2008-01-22
> **cwmoser said:**
> Mine turned out to *not* being a hardware issue.  Instead, it was corrupted X configuration.


Yeh. I think too that my problem isn't hardware. But file corruption is something that I can't tolerate.

I did run several test and yet, no problems at all.

I think that software might be broken somehow? Write cache flush at shutdown or something like that missing or failing?

Yesterday I did run several tests for my hardware, no problems what so ever. And I still suffer from bootups and corrupted files. Maybe it's software that should be blamed?

---

### Post by Ux64 on 2008-01-23
Ok, my fstab was bad. So now my system boots. But data still get's corrupted when shutting system down.

I wonder if cache flush could fail?

---

