---
title: "[SOLVED] Repartitioning with DiskUtiltiy - no MS-DOS (FAT32) option"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by rwallace on 2008-11-05
Hey all,

I'm trying to get a triple boot system setup on my new Mac Pro.  I might have to start things over because I had to install Ubuntu before installing Windows XP because I didn't have a disk handy.

But before I start over I want to try and get this working.  When I did the install I resized the Mac partition and created a partition for the Linux ext3 / filesystem, a Windows partition and a Linux swap partition.

But in DiskUtility I could, and currently can, only create "Mac OS Extended (Journaled)" partitions.  It won't let me select a different format, such as MS-DOS (FAT32).

So, I guess I have a couple of questions.

1) Do I need to start over and just wipe out the existing Linux partitions?

2) Why is there no MS-DOS (FAT32) option in DiskUtility and how can I make it an option so I can create the Windows partition in DiskUtility (I'd rather not have to use BootCamp if I don't have to)?

Thanks,
Rich

---

### Post by cyberdork33 on 2008-11-05
i would just create an OSX partition and one other partition that takes up all the space you will need for windows, ubuntu, and the swap. Then boot the Ubuntu LiveCD and delete the partition and create your desired partitions in its place.

---

### Post by rwallace on 2008-11-05
Oh.  I was operating on what you wrote on <[this thread]("http://ubuntuforums.org/showpost.php?p=5928800&postcount=6")>.  I didn't want to disturb the Windows partition after it had been created for fear of messing something up.

---

### Post by cyberdork33 on 2008-11-05
> **rwallace said:**
> Oh.  I was operating on what you wrote on <[this thread]("http://ubuntuforums.org/showpost.php?p=5928800&postcount=6")>.  I didn't want to disturb the Windows partition after it had been created for fear of messing something up.
It is messing with the partitions at all after Windows is installed that seems to be the issue, but you are correct for the most part.

I am not sure why Disc Utility is not allowing you to create an msdos partition. After you create the partition you may be able to use the 'erase' tab when the partition is selected in order to reformat it to msdos.

---

### Post by rwallace on 2008-11-05
Well, I think I figured out the problem.  It seems that booting from the already installed OS X and using DiskUtility won't let you create MS-DOS partitions, but I booted from the install CD and was able to do it just fine.

Thanks for the help,
Rich

---

### Post by rwallace on 2008-11-05
> **cyberdork33 said:**
> i would just create an OSX partition and one other partition that takes up all the space you will need for windows, ubuntu, and the swap. Then boot the Ubuntu LiveCD and delete the partition and create your desired partitions in its place.

Ok, I did as you suggested letting Bootcamp create the second partition.  But after doing the Windows install from the CD and trying to continue the install from the hard drive, I select the Windows partition in the reFIT boot screen and then it just hangs with a gray display and a dark gray Windows logo.  Any idea what I screwed up now and how I can fix it?

---

### Post by cyberdork33 on 2008-11-05
> **rwallace said:**
> Ok, I did as you suggested letting Bootcamp create the second partition.  But after doing the Windows install from the CD and trying to continue the install from the hard drive, I select the Windows partition in the reFIT boot screen and then it just hangs with a gray display and a dark gray Windows logo.  Any idea what I screwed up now and how I can fix it?
Make sure that your partitions are in sync with the partition tool in the rEFIt menu.

---

### Post by rwallace on 2008-11-05
> **cyberdork33 said:**
> Make sure that your partitions are in sync with the partition tool in the rEFIt menu.

Yup, did that.  No help.  When trying to boot windows it seems like it never transfers control to the OS.  Just hangs on the gray screen with the gray windows logo.

---

### Post by cyberdork33 on 2008-11-05
> **rwallace said:**
> Yup, did that.  No help.  When trying to boot windows it seems like it never transfers control to the OS.  Just hangs on the gray screen with the gray windows logo.
Ok. Try this. I don't know if it will work, but I have seen something similar, just not with windows...

shutdown the machine completely (not reboot) and then turn it back on again a couple of times. That seems to fix the freezing thing for some reason.

---

### Post by rwallace on 2008-11-06
Holy cow that worked!!!

In the end I did wind up doing a complete reinstall of OS X and starting from scratch while awaiting your response.  I still got stuck on the gray screen of death after installing from the CD.  But shutting down once and then trying again worked like a charm.  Weird.  

Thanks!
Rich

---

### Post by cyberdork33 on 2008-11-06
> **rwallace said:**
> Holy cow that worked!!!

In the end I did wind up doing a complete reinstall of OS X and starting from scratch while awaiting your response.  I still got stuck on the gray screen of death after installing from the CD.  But shutting down once and then trying again worked like a charm.  Weird.  

Thanks!
Rich
Great! At least now I will know that can fix it.

Please mark this thread as solved fromt he thread tools menu at the top of the page if everything has been addressed.

---

