---
title: "NTFS partion?"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by JoeZ on 2006-01-07
I'm thinking of switching to Ubuntu from Windows...
But I have one more question...
What does it mean with NTFS when they say can read and copy, but not write?
Does this mean, when I write something in a document on a separate NTFS partion I cant save the file because it is on a NTFS partion?
Or when I download something I cant save it on a NTFS partion?

---

### Post by JW_00000 on 2006-01-07
Linux can't write to NTFS partitions, Windows can. NTFS is the default filesystem for Windows, but (I think due to patenting issues) Linux or any other OS can only read it, but not write to it. Ubuntu recommens ext3 as filesystem type.
So, probably the best is to back all your files up on a cd/dvd, then install Ubuntu with ext3, and then copy everything from the cd.
You could also leave the NTFS partition as it is, and install Ubuntu on another partition, but then you need to copy every file you want to edit that's on the NTFS partition, and save it on the other partition.

---

### Post by JoeZ on 2006-01-07
So this means that my 200GB of information etc. I will only be able to read?...
Okey!... This is gonna be some hard task... But I will make things work out ;)...

---

### Post by JW_00000 on 2006-01-07
If you need to copy 200GB, it's probably better not to use CD's (you'll need over 200) or DVD's (also at least 50). You can try to connect your computer with another one, if you're in a network that's perfect. When I switched to Ubuntu, I copied the data over a Windows network, using shared folders (everything was already configured though).
If this *really* isn't possible, you can also try to connect your hard drive with another computer and copy everything to there, then reformat the hard drive to ext3 and copy everything back on it.
But, I just think about this, if it are 2 hard drives, you have no real problem. Than, you can just format the first one, install Ubuntu on it, and copy data later (at least if the first drive is as big as the second...)
Good luck!
Edit: Or, if you or someone you know has an external hard disk?

---

### Post by ysse on 2006-01-07
One common way of sharing information between Linux and Windows is to create one or more FAT32 partitions where you keep files you want to access from both worlds. This, of course, is assuming that you mean to dual boot, and not switch entirely.

---

