---
title: "Windows Files onto External Ubuntu HD"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by The AlGorenator on 2007-03-15
How can i access my windows files from ubuntu?

just as a note, my ubuntu boots of an external HD. i assume that makes a difference, as i searched teh forum and only found things about getting win files of a partition.

---

### Post by AtrejuT on 2007-03-15
can you post what
```

sudo fdisk -l

```
gives you?

atreju

---

### Post by finer recliner on 2007-03-15
don't cry.

try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by The AlGorenator on 2007-03-15
[code]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        9728    78075900    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60424   485355748+  83  Linux
/dev/sdb2           60425       60801     3028252+   5  Extended
/dev/sdb5           60425       60801     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 521 MB, 521142272 bytes
32 heads, 32 sectors/track, 994 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         994      508911+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(992, 31, 32) logical=(993, 31, 31)
[code]

that's what i get, the 500 is the disk i've got ubuntu running off, the 80 is the one with my windows files.

---

### Post by The AlGorenator on 2007-03-15
> **finer recliner said:**
> don't cry.

try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

i tried that, i couldn't gettit to work.

---

### Post by AtrejuT on 2007-03-15
ok, so what we try to see if this works is:
```

sudo -i
mkdir /media/windows
mount /dev/sda2 /media/windows
cd /media/windows
ls

```

and see if that's what you need.
question: will you need to be able to write to your ntfs partition, or only read?

atreju

---

### Post by The AlGorenator on 2007-03-15
That brought up a list of the files in my main drive (the main directorys anyway) in the console, so yes, it think i did work - i still do not know how to access [should that have done it?]

yeah, i would like to be able to write to it, but if it's impossible, i can live without it.

---

### Post by eljalill on 2007-03-15
You can write on a ntfs partition or hard drive, when you install the ntfs-3g , it's in synaptics.

---

### Post by AtrejuT on 2007-03-15
That means you can read your files, yes.
However we now should set it up in a way that it is mounted automatically whenever you boot, and such that you can write to it. As eljalill pointed out you need to install ntfs-3g for this first. This should be easy using synaptic.
I think the easiest way, rather then me explaining it all is to follow this guide:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

If you have questions, ask, though!

atreju

---

### Post by The AlGorenator on 2007-03-15
i've gonw through all teh steps in that guide, but i still cannot see my internal HD in the computer folder.

have i done something wrong, or is there a command i have to ebter?

---

### Post by AtrejuT on 2007-03-15
what happens if you navigate to /media/windows (if that is the folder name you used)

atreju

and did you follow the auomatic or the manual way in that howto?

---

### Post by The AlGorenator on 2007-03-15
oh, sorry, don't worry about it. 

i've got it going now. THANKS HEAPS!!!

also, do you know how i can make my external HD accesable from windows [windows recognises it but will not let me do anything to it] - if this is the wrong place to ask, thanks for all teh rest of the help.

---

### Post by AtrejuT on 2007-03-15
if you formated as as ext3 you will need to use the driver from
[http://www.fs-driver.org/](http://www.fs-driver.org/)
have fun

atreju

---

### Post by The AlGorenator on 2007-03-15
Dear AtrejuT,

i LOVE YOU SO MUCH!!!!!!

THANKYOU HEAPS!!!!!

yours sincerely, 

the algorenator aka jimmy.

---

