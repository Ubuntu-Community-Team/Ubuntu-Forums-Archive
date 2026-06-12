---
title: "Halp with new Slave Drive"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by childofstrings on 2008-01-04
Hello lovely Ubuntu people,

Let me give you a little background on my problem before I get to the meat of my question.

I am currently running Windows XP with SP2 on my Master HDD. A couple of months ago, I decided I wanted to try out Ubuntu by installing it on a crappy 15GB HDD I had lying around. I went about setting the drive to slave and it showed up fine in my computer. I went ahead and installed Ubuntu and everything was fine and dandy. I continued using XP as my default OS and had Ubuntu around for experimentation.

Well, my master drive began running out of space, so I went ahead and ordered a new HDD. I didn't have any important data on the 15GB HDD, so I didn't bother formatting it or anything before installing the new one. 

Well, I pop in the new HDD and boot my computer, but I get a Grub Loader error before it will even boot XP. I was suprised at this because I thought I had only installed Ubuntu on my old 15GB HDD, so why was the Grub Loader showing up at all, when my old slave drive isn't even in the computer? But anyway, I figured maybe this was because I needed to format the old HDD or something. So I go back and put in the old HDD and delete the partitions on it. I didn't see an option for formatting, so I just deleted the partitions on it and assumed that would take care of it. Not so.

I put in the new HDD again and I still get this Grub Loader error!!! Well, finally I just pop in my Ubuntu Live Disk and I go ahead and install Ubuntu onto my new Slave HDD. I was planning on doing it anyway, so no big deal.

So now I've got Ubuntu on my slave drive, and I am able to get into XP, but I've got all these files that I want to transfer to my new drive and when I look for my new HDD in Disk Management, all it shows me is the partitions and it wont let me format, assign a drive letter, etc etc.

What do I need to do in order to make this new HDD Show up in Windows XP to transfer my files? Preferably without having to get rid of Ubuntu. However, if I need to get rid of Ubuntu to get my files on the new HDD, Im willing to do it. Please help! Im sick of getting these damn "low disk space" warnings from Windows!!!

Thanks for your help!

---

### Post by eternicode on 2008-01-04
> **childofstrings said:**
> so why was the Grub Loader showing up at all, when my old slave drive isn't even in the computer?

When you installed Ubuntu, the install program most likely installed the GRUB bootloader onto the Master Boot Record of the master HDD, overwriting the Windows MBR.

> **childofstrings said:**
> So I go back and put in the old HDD and delete the partitions on it.


Deleting the partitions is similar to formatting, except that there is no filesystem to use afterwards.  In GParted, you can right-click a partition, then go to "Format as"->fs-type.

The GRUB bootloader was most likely looking for files on one of the partitions you deleted.

> **childofstrings said:**
> I put in the new HDD again and I still get this Grub Loader error!!! Well, finally I just pop in my Ubuntu Live Disk and I go ahead and install Ubuntu onto my new Slave HDD. I was planning on doing it anyway, so no big deal.

This will have re-written the GRUB to look for the newly available files.

> **childofstrings said:**
> So now I've got Ubuntu on my slave drive, and I am able to get into XP, but I've got all these files that I want to transfer to my new drive and when I look for my new HDD in Disk Management, all it shows me is the partitions and it wont let me format, assign a drive letter, etc etc.

Linux's native filesystem format(s) are not readable by Windows.  You will have to repartition the new drive to have either a FAT32 partition or an NTFS partition to put your data on.  Again, this can be done with GParted, but you will have to do it from a livecd.

> **childofstrings said:**
> What do I need to do in order to make this new HDD Show up in Windows XP to transfer my files? Preferably without having to get rid of Ubuntu. However, if I need to get rid of Ubuntu to get my files on the new HDD, Im willing to do it. Please help! Im sick of getting these damn "low disk space" warnings from Windows!!!

Thanks for your help!

You can repartition the drive with a livecd using GParted, as I mentioned earlier.  Or you can wipe Ubuntu, fix the MBR, and make the second drive windows-readable (FAT32 or NTFS).

The signature from [this post]("http://ubuntuforums.org/showpost.php?p=4025588&postcount=5") has various MBR and bootloader resources.

---

### Post by childofstrings on 2008-01-04
I just went through in windows and deleted the Ubuntu partitions and Im now formatting in windows since its the operating system I know best. I see now why I wasn't able to get into windows before, and Im currently setting aside a partition for Ubuntu, which Im planning on re-installing after I post this reply.

Everything should be ok now. Thanks so much for your help!

---

### Post by eternicode on 2008-01-04
Great :) post back if you have any troubles.

---

