---
title: "backing up a whole partition"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by RAPMX on 2008-03-14
Hello.
This is my first thread as i'm completely new Linux (I've learned some reading the threats but that's all).

Let me explain the whole story.
Some time ago following this thread: [http://ubuntuforums.org/showthread.php?t=80811&page=51](http://ubuntuforums.org/showthread.php?t=80811&page=51) I successfully installed Ubuntu on an 80 GB external HDD. Then upgraded to 7.10 without any problems.
Now I have a new external 500GB, I would like to do the follow:

1.- Install Ubuntu in a 80GB partition. (So I can boot from external HDD)
2.- Make 2 additional NFTS partitions.
3.- The most important thing, I would like to make an exact copy of my old 80BG external to a partition on the new 500 GB HDD to avoid install from the beginning making all the adjustments I did to make it work.

I tried making a boot cd with System Rescue on it. Then I used GParted to make an exact copy of the partition in my old external HDD. But after copying the partition and rebooting from the new 500GB HDD I got Error 17.

I also read about using Partimage, but I could not complete the process, I guess I did not know how to mount properly (I-m not experienced with commands). But, anyway, Im wondering if I would get the same Error17 after completing the backing up process with Partimage.

Any help will be very appreciated, just remember Im very new and not familiar with commands, so please be very explicits with any command.

Thanks in advance to all.

Regards.
:)

---

### Post by t0p on 2008-03-14
Regarding backing up a partition:  There's an app called **pybackpack** that you can use to do it.  Get it through Synaptic (**System > Administration > Synaptic Package Manager**).

Hope this helps!!

---

