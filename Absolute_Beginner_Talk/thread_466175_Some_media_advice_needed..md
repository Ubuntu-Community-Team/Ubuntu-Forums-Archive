---
title: "Some media advice needed."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Volsfan91 on 2007-06-06
Right now, I'm in a dilemma because I need to figure out how to manage my media between my dual boot Windows XP and Ubuntu.

All of my media (music, photos, videos) are currently on my NTFS partition. Although I know that Ubuntu has built in NTFS read support, I found that it's a bit slow on my older machine.

So how does this sound:

I borrow about 30 gigs from my current XP partition for a new FAT32 partition where all of my media will be stored.

What do you guys think?

---

### Post by jonward0690 on 2007-06-06
That is how I do things on my pc but it is only a 10GB partiton.

---

### Post by Songwind on 2007-06-06
That should work.

We just had a similar problem at my house, though it was more about redundant files on several computers.  We put them all on an Ubuntu server machine and shared to the Ubuntu boxes and the Windows boxes with SAMBA.

---

### Post by Songwind on 2007-06-06
I also found that once I was comfortable in Linux again I stopped ever watching those media files in Windows. :)

---

### Post by p_quarles on 2007-06-06
Sounds good, but make sure that you still have more than the minimum required free space on the XP partition. Windows needs a fair amount of space for virtual memory and so forth. 

From what I know, too, you may not have much better luck with a FAT partition. It's a pretty inefficient file system, and could conceivably be slower than NTFS. Haven't tried it, though, so I don't know.

The other thing is that I believe there's a way of making Windows capable of reading ext3 files. You might look into that as well.

---

### Post by Volsfan91 on 2007-06-06
Thanks a lot for all of the help guys... However, I'm still not real sure what to do. Maybe I just won't listen to music much when I run Linux?

---

### Post by Songwind on 2007-06-06
If it were me I would leave them on the NTFS partition and install the ntfs-3g driver.

---

### Post by akschnare on 2007-06-06
I have a Windows partition a Linux partition and a Storage partition that is Fat32. Both Windows and Linux can see the Storage partition and it works flawlessly. I'm a beginner with Linux and it is easy to do.

---

### Post by logos34 on 2007-06-06
> **Volsfan91 said:**
> Right now, I'm in a dilemma because I need to figure out how to manage my media between my dual boot Windows XP and Ubuntu.

All of my media (music, photos, videos) are currently on my NTFS partition. Although I know that Ubuntu has built in NTFS read support, I found that it's a bit slow on my older machine.

So how does this sound:

I borrow about 30 gigs from my current XP partition for a new FAT32 partition where all of my media will be stored.

What do you guys think?

There's a lot easier way.  NTFS-3G is a driver for linux that adds write support for NTFS.  Open a terminal and type:

sudo apt-get install ntfs-3g ntfs-config

(the latter is a easy to use gui that will automatically edit your fstab file to mount ntfs r+w (using fuse module.  Just open apllciations>system tools>ntfs config and tick the boxes).

To add ext3 read+write capability to winxp, get [B][fs-driver[]("http://www.fs-driver.org/")/B].

Good luck!

---

### Post by hillbilly on 2007-06-06
I organize my media like:
Music:
 have all the musicfiles on Windows, which is an NTFS partition. I mount these ntfs partitions as read only on linux and listen to them. I don't do any sort of music editing, and in case I need to edit the tags for these files, i log into windows. Its dumb, but I dont want to transfer all the music from my windows partition to my linux partition and resize the existing partitions e.t.c. and anyway, I usually don't have to modify my tags and Amarok handles the music on the Windows drives without a problem. Amarok rocks :D !

Photos:
I have been searching around for a good Linux Photo Management Software, but I have not been able to find any so far, so all my photos are on the Windows partition. I won't be be transferring my Photos to my Linux partition as Photos take up much of my hard drive and transferring them from one partition to another is bound to be risky for me (ok, its too much of a pain and I'm lazy ;) !)

Videos:
All my videos are on the linux partition.

I like Songwind's solution though and as soon as I can get some new hardware, thats what I'm going to do. Although till I find a decent enough Photo Management Solution on Linux that I'm comfortable with, my photos will still remain on the Windows partition.


Oh  forgot to mention; I have another 2 GB (yeah 2 !!) FAT32 partition where I store files that need to be written to from both Linux and Windows. Serves my purpose admirably.

---

### Post by Songwind on 2007-06-06
Have you tried fspot and digiKam?

---

### Post by ajgreeny on 2007-06-06
>  Although till I find a decent enough Photo Management Solution on Linux that I'm comfortable with, my photos will still remain on the Windows partition.



When you say "Photo Management Solution" do you mean management, or editing?  I agree **gimp** takes a bit of practice for edits, but **f-spot** or **digikam** for management are both top notch apps.  Just my opinion, I accept, but many others agree.

---

### Post by hillbilly on 2007-06-06
I don't want to hijack this thread but I will just mention that, I did try f-spot and digiKam and found them wanting. Main reason was they required me to duplicate my photos (had to do this since I did not make my ntfs write able.) Right now I use Picasa and although its not very good, its sufficient for me right now. (Was concerned only with management, for editing I use gimp.)

---

### Post by p_quarles on 2007-06-06
FYI, you CAN use Picasa in Linux. Google has a package that is preconfigured to run through Wine.

---

