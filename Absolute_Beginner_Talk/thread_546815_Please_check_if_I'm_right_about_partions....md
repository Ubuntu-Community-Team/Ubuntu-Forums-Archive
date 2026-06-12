---
title: "Please check if I'm right about partions..."
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-09-09
\  is  where Ubuntu is installed.  Not sure if this is where programs go as well.  Could be.  What about tarballs?

\home is personal files. 

Good to have the two separate so you can change "\" for a newer version.  If you have the "\home" inside the "\" then you can't do that (which is what I have I think).  

Is that right?

---

### Post by aberadam on 2007-09-09
*Partitions.

---

### Post by Bothered on 2007-09-09
See [here]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") - and yes, that's right. If you have a separate home partition, you can reinstall to / and retain your documents etc., or install another operating system and share the same home partition.

---

### Post by rich.bradshaw on 2007-09-09
Pretty much - perhaps oversimplified but yeah.

/home on a seperate partion means you can update/install linux again without losing documents.

Equivalent to putting My Documents on a seperate partition in Windows.

---

### Post by Steveway on 2007-09-09
Yes and don't forget.
It's / and not \.
Windows changed it to \, I don't know why but everywhere else we use /.

---

### Post by aberadam on 2007-09-09
Great, thanks.

---

### Post by aberadam on 2007-09-09
Ok, right, / not \, another question:  If when installing don't specifically create a /home partition it will be made inside the normal /, so //home in  a way?

---

### Post by sumguy231 on 2007-09-09
Linux uses a single hierarchical filesystem structure, so / can actually contain many different partitions under it. The directory where a partition or filesystem is "attached" to is its mountpoint. You can mount a partition almost anywhere, so you could also have /etc be a separate partition if you wanted to. So your home partition is mounted to /home, while your system partition is mounted to just /.

---

