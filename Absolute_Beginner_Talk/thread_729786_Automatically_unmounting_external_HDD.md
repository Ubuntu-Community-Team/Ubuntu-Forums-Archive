---
title: "Automatically unmounting external HDD"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by coderdb on 2008-03-20
My external HDD (it's formatted in NTFS if this makes a difference) seems to automatically unmount itself after a period of inactivity. Is there a way to stop this from happening? I've had a quick look through the power settings and there didn't seem to be anything in there related to HDD management.

I'm not manually mounting it either, it mounts automatically when the system starts.

---

### Post by sayakb on 2008-03-20
Do you have USB autosuspend ON? Check for value usbcore.autosuspend in your kernel config. 
Plus, this might not be a solution, but should work. If you use Rhythmbox or Banshee, add a few files from your external HDD to their library, so that the drive could not unmount unless the music player is closed.

---

### Post by ajgreeny on 2008-03-20
There are some newer Seagate drives which can be a problem if I remember right, as they shutdown automatically after a period of inactivity and can be difficult to bring to life again without unpluging and repluging.

---

### Post by jago25_98 on 2008-03-20
investigate

/etc/hdparm.conf

and

hdparm --help

to see if sleep options help, or whether the hardware has it's own thing going on

---

### Post by jdong on 2008-03-20
Would you by any chance have a Seagate FreeAgent external?

---

### Post by jago25_98 on 2008-03-20
nope

---

