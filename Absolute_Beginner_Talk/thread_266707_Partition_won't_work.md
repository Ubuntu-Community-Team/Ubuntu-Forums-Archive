---
title: "Partition won't work"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-09-27
I have a FAT32 partition so both windows and Linux can get into them.  I store music and documents on it.  But I can't get into it from linux.  It shows up, but it says "error: device /dev/hda2 is not removable

error: could not execute pmount."

Not cool.  Is there a way to fix it?

---

### Post by divague on 2006-09-27
can you show your /etc/fstab file?

---

### Post by bodhi.zazen on 2006-09-27
> **WADemosthenes said:**
> I have a FAT32 partition so both windows and Linux can get into them.  I store music and documents on it.  But I can't get into it from linux.  It shows up, but it says "error: device /dev/hda2 is not removable

error: could not execute pmount."

Not cool.  Is there a way to fix it?

Yes.

```
sudo mkdir /mnt/music
```
Call it what you will but put it in /media if you want a desktop icon, /mnt if you do not.

Now to mount:```
sudo mount -t vfat /dev/hda2 /mnt/music
```

To have it mounted at boot, rw access for users:
```
sudo gedit /etc/fstab
```

Add this line:```
/dev/hda2  /mnt/music  vfat  auto,users,rw  0 0
```

Now unmount and re-mount:```
sudo umount /mnt/music
mount /mnt/music
```

Note: no sudo in that last mount command.

:cool:

---

### Post by WADemosthenes on 2006-09-28
> Call it what you will but put it in /media if you want a desktop icon, /mnt if you do not.

Do I just drag and drop it in there? (sry, thought I was getting good at linux :P).

---

### Post by bodhi.zazen on 2006-09-28
Not quite.

By call it what you want I am referring to the "music" part.

You could call it:
/mnt/music
/mnt/data
/mnt/audio

Now that you have a name,

sudo mkdir /mnt/name (no desktop icon with this option).

or 

sudo mkdir /media/name (if you want it on your desktop).

I used "/mnt/music" in my example. If you use something different adjust the line in fstab accordingly.

I know it is confusing at first, it gets easier....

HTH

---

### Post by WADemosthenes on 2006-09-28
I got all the way to the end, but on the cammand to remount ("mount /media/music" -- I chose media) it said:
"mount: can't find /media/music in /etc/fstab or /etc/mtab"

---

### Post by bodhi.zazen on 2006-09-28
LOL :lol:

You must have a typo somewhere.

Can you post your fstab?

---

### Post by Bachstelze on 2006-09-28
Did you add the line in /etc/fstab as was mentioned earlier ? Do not forget to change /mnt/music to /media/music of course.

---

### Post by WADemosthenes on 2006-09-28
I looked at the fstab file and it had "/mnt/music" so I changed it to media, I followed the directions again, and it's working fine (not on desktop, but that's okay).

Thanks guys!

---

