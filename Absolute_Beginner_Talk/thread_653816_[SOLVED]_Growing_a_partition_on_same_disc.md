---
title: "[SOLVED] Growing a partition on same disc"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by rtrdom on 2007-12-30
I have sda1(Windows), sda2 (Linux 97% full), sda3 (swap/solaris) and sda4 (Linux 1% used.  How can I expand sda2 to include the space available in sda4?
Thanks for any response.

---

### Post by overdrank on 2007-12-30
> **rtrdom said:**
> I have sda1(Windows), sda2 (Linux 97% full), sda3 (swap/solaris) and sda4 (Linux 1% used.  How can I expand sda2 to include the space available in sda4?
Thanks for any response.

Hi and this is a good thread on partitioning
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
Good luck!

---

### Post by rtrdom on 2007-12-30
Thanks for the response.  I checked each of the references but found nothing 
that would help resize a full drive into one nearly empty, without removing something.
I really want to keep the data that is in sda2.  Am currently looking for a good way to
back it up, then restore it into a reformated drive.
Thanks again for the response.

---

### Post by indytim on 2007-12-30
What's on sda4?

IndyTim

---

### Post by eternicode on 2007-12-30
> **rtrdom said:**
> Thanks for the response.  I checked each of the references but found nothing 
that would help resize a full drive into one nearly empty, without removing something.

Just to be clear, you resize *partitions* on a drive, not the drives themselves :)

> **rtrdom said:**
> I really want to keep the data that is in sda2.  Am currently looking for a good way to
back it up, then restore it into a reformated drive.
Thanks again for the response.

If you have a separate (empty?) drive to which you can backup, you can do a [dd/gzip backup]("http://wiki.linuxquestions.org/wiki/Dd#Getting_around_file_size_limitations_using_split").  Also you could use partimage (available on the [SysRescCD]("http://sysresccd.org")).

Are you planning to use GParted?

I would say that the method you use would be dependent on the physical order of the partitions on the disk.

Could you open GParted in your current linux installation and post a screenshot of its /dev/sda display?

If not, post the output of "sudo fdisk -l"

---

### Post by rtrdom on 2007-12-31
Thanks you all for the responses.  I just now got things back together. This problem
I solved the HARD way but I no longer have windows on this machine. I carefully removed all the data via 8GiB thumbdrive and stored it in sections on another machine.
Then, I used my Ubuntu CD as a live CD to reformat and partition the drive. Afterwards
I shutdown the laptop, with CD in it, rebooted the machine, installed Ubuntu 7.10, and
commenced returning things to their proper place. All is well, now on 31 Dec 2007.
May all of you have a very happy new year.:)

This problem is solved.

---

### Post by eternicode on 2007-12-31
> **rtrdom said:**
> Thanks you all for the responses.  I just now got things back together. This problem
I solved the HARD way but I no longer have windows on this machine. I carefully removed all the data via 8GiB thumbdrive and stored it in sections on another machine.
Then, I used my Ubuntu CD as a live CD to reformat and partition the drive. Afterwards
I shutdown the laptop, with CD in it, rebooted the machine, installed Ubuntu 7.10, and
commenced returning things to their proper place. All is well, now on 31 Dec 2007.
May all of you have a very happy new year.:)

This problem is solved.

Hehe, alright, glad you got it sorted out.

Could you mark the thread as "Solved"?  You'll find the option under "Thread Tools" to the right, above your first post.

And Happy New Year's :popcorn:

---

