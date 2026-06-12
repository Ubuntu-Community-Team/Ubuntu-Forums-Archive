---
title: "How can I access my other hard-disk? (it's Windows XP on it)"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by ArnsteinK on 2007-03-12
I want to access my other hard-disk so that I can listen to the music I have on it! How do I do this?

---

### Post by bernied on 2007-03-12
Maybe [this](http://www.psychocats.net/ubuntu/mountwindows) will help?

---

### Post by lamalex on 2007-03-12
You should be able to read your ntfs partition. If you can't try installing linux ntfs drivers from [http://sourceforge.net/projects/ntfs-3g](http://sourceforge.net/projects/ntfs-3g)

---

### Post by OffHand on 2007-03-12
> **Iamalex said:**
> You should be able to read your ntfs partition. If you can't try installing linux ntfs drivers from [http://sourceforge.net/projects/ntfs-3g](http://sourceforge.net/projects/ntfs-3g)

Not needed for reading, only for writing.

---

### Post by ArnsteinK on 2007-03-12
Thanks! But how should line 1 of the fstab-file look like? I accidentally edited it so it says [mntent]: line 1 in /etc/fstab is bad

---

### Post by bernied on 2007-03-12
Show us what line 1 looks like now and what drives you have mounted (2 commands):
```
cat /etc/fstab
mount
```

Do not turn off your computer until you have this sorted.

---

### Post by bernied on 2007-03-12
A little explanation. The fstab file is different for every computer, so I can't tell you what yours should look like. It controls which devices are mounted on the filesystem and where.

Even though you have lost a line of the file, we can probably reconstruct it, knowing what is already mounted and where (the output of the 'mount' command).

If you restart your computer, whatever was on line one will not get mounted, and it's pretty safe to say that the first device to be mounted is probably important.

---

### Post by ArnsteinK on 2007-03-12
"
/etc/fstab: static file system information."

this is the top of the file (without the "s)

---

### Post by bernied on 2007-03-12
OK, that's easy, that line should be a comment, so just add a # at the start.

---

### Post by ArnsteinK on 2007-03-12
OK, I did it and it worked, but I still can't see E: (which is the hard-disk with Windows)

---

### Post by bernied on 2007-03-13
> **ArnsteinK said:**
> OK, I did it and it worked, but I still can't see E: (which is the hard-disk with Windows)In linux it won't be called E: it will be called whatever you chose to call it. If you followed that guide then it will be at /windows. You can type that into your file browser and it should come up.

If you want the device to appear on your desktop then you need to put it in the /media directory. Just create a new mountpoint 'sudo mkdir /media/windows' and change the fstab so that the bit saying '/windows' says '/media/windows'. You might also want to remove the old dir, use 'sudo rmdir /windows' (this will only remove an empty directory, which is just as well)

---

### Post by ArnsteinK on 2007-03-14
rmdir: /windows: Device or resource busy

this is what it says! What do I have to do? Thanks for helping me!

---

### Post by bernied on 2007-03-15
> **ArnsteinK said:**
> rmdir: /windows: Device or resource busy

this is what it says! What do I have to do? Thanks for helping me!
This means that you have the folder open somewhere, somehow. Maybe you are at that directory in a terminal, or you have it open in nautilus or similar, or maybe the system is still trying to mount the windows partition on it.

The easiest way to deal with this is to restart, then try to delete it again. But check that you are no longer pointing to /windows in your fstab file before you do.

---

