---
title: "partition question."
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by funkey+junkie on 2007-02-13
So i've decided to make the leap to open source, but i'm not too familiar with partitioning.

When defraging my drive windows reported "unmovable files", my question is, will those files interfear  with my partitioning?

---

### Post by Ziox on 2007-02-13
whether those files will interfere with your patitioning is decided by the location of those files.  If the files span the entire partion, like so: [*****____*__*____***], then most likely, you cannot partition it.  Or if you are lucky, the partition is extremely small.
However if the files are placed like so: [*******____*_______], then you can create a larger partition from the free space behind the last file (*).
If you are files do span the entir partition (or close to).  I would suggest installing and defragmenting the parition with another software.

---

### Post by jpeddicord on 2007-02-13
To add to the above poster: If it said that some could not be defragmented, then you will need to boot into Safe Mode for these to defragment properly. Right before you see the Windows logo, hit F8. Select Safe Mode from the menu. The system will boot, but without all of the bells and whistles. Do a defragment in this mode and you should be all right. :) 

Jacob

---

### Post by sacedric on 2007-02-13
Are you looking to remove Windows first? Why not first try set up a dual boot system? Or maybe you are and its on the intended Ubuntu partition you have the unmovable files. I would suggest rying somethng like pArtition MAgic and see if you can set up the partition that way.

---

### Post by funkey+junkie on 2007-02-13
Thanks for the replies.  Going dual boot is indeed the route I intended to go, sorry for the lack of info, and since the files are spread across the hard drive as Ziox has stated, i was wondering if it is possible to run the os's on differant hdd's.

---

### Post by coolen on 2007-02-14
It is indeed. If you have any, plug them in, and install to that drive. It should be fairly clear which one is which, but it'll probably come up as hdb, or perhaps hdc (assuming you have a CD or DVD drive, and depending on how it's connected). This should be fairly obvious in the installer.

---

### Post by housam on 2007-02-14
> **funkey+junkie said:**
> Thanks for the replies.  Going dual boot is indeed the route I intended to go, sorry for the lack of info, and since the files are spread across the hard drive as Ziox has stated, i was wondering if it is possible to run the os's on differant hdd's.


If you have only one HDD , defrage it 2-3 times ,then locate where is the green mark for the unremovable files ( it is the windows file system ) and resize the partition from its end to just before that mark ( use Gparted to do the task - it is on the live CD). This 'll create an unallocated space which can be divided into 2 partitions : one for the root ( / ) ext3 format ( 5-10 Gb ) and the other is for the swap partition ( 1 Gb ) swap sormat. then go for the installation . when it comes to the partition ( step 5 ) choose the manual way.

Good luck

---

