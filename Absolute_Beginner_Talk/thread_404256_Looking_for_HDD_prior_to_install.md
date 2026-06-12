---
title: "Looking for HDD prior to install"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by cloud1494 on 2007-04-08
I'm trying to access my windows HDD before I install Ubuntu. My HDD is not in /mnt, can you tell me where it might be?

---

### Post by siciliancasanova on 2007-04-08
If your trying to do some partitioning/resizing etc... I would suggest using the [gparted live cd]("http://gparted.sourceforge.net/livecd.php").

Are you trying to access files, or format your HDD?

---

### Post by cloud1494 on 2007-04-08
I'm just trying to access files. Will I be able to access NTFS partitions?

---

### Post by siciliancasanova on 2007-04-08
I'm not quite sure what you're exactly trying to do.  If you're in Windows now, you are running and able to view your files on the NTFS partition.  

Can you be more specific

---

### Post by cloud1494 on 2007-04-08
Yeah, I just booted the disc and I'm trying to view some of my windows files from inside ubuntu. I've tried mounting the disk already, but it tells me I can't access it. Is there a special program I need in order to view windows partitions?

---

### Post by gasolinehabit on 2007-04-08
did you try "sudo mount -a" to actually mount the drive?

---

### Post by cloud1494 on 2007-04-08
I didn't do that, let me try it real quick....

Tried it, didn't work, says "mount: /dev/hda2: can't read superblock"

---

### Post by confused57 on 2007-04-08
If you're trying to mount the drive from the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

