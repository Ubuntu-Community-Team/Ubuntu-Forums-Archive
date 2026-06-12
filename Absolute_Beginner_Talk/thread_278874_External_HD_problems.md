---
title: "External HD problems"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-10-17
I have a 300 gig external hard drive but it was formatted in windows for windows use so it is NTFS.  I can read it (listen to music and watch videos) but I cant write anything onto it through Ubuntu.  Is there anything I can do to fix this that doesnt involve reformatting it and losing all my files that are stored on the external HD?

---

### Post by viper on 2006-10-17
Hi, you could down load this live cd. GParted live CD from this link [http://www.linux.com/article.pl?sid=06/04/25/1917228](http://www.linux.com/article.pl?sid=06/04/25/1917228)
Then resize your partition, create another partition to  Fat32 move your stuff across then format the oricinal partition to fat32 also that way you just plug n play all over the place eg windows linux etc. Hope this helps.

---

### Post by familyjules74123 on 2006-10-17
fat32 is read and writable by both systems?

---

### Post by ciscosurfer on 2006-10-17
You can check out this thread to enable you to use your NTFS formatted drive like you would your EXT3 Ubuntu file system (copy, paste...mainly allowing you to paste things into that drive from your Ubuntu drive.)  It's very useful for me as I use it (my NTFS drive) to back up stuff from Ubuntu (i.e., when I'm reformatting Ubuntu and want to keep my current settings, etc.)  It involves using a program called fuse and ntfs-3g. The orginal poster (OP) of the thread says that the software is still beta.  While this might be true, I've no problems using it and I've been using it since June of 2006.  Here's the link: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

And yes, FAT32 (seen and used by Ubuntu as file system type VFAT) is read/writeable by Ubuntu.  Make sure you have your /etc/fstab setup correctly though.  Check here: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by familyjules74123 on 2006-10-18
thank you for giving me the link to that tutorial thread, it worked and was relatively easy to get working.

---

