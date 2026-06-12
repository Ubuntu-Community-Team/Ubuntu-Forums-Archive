---
title: "Where's the kernel? New install on G3 has I/O error."
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by mcruser on 2005-09-25
Hi, all -

Hope you're having a good day out there. I'm a newbie with a Mac, so those forums may also be applicable, but this sounded primarily like an installation question, so it's landed here.

I'm installing Linux for the first time on my Mac b&w G3 (yosemite revision 1 model) on a new HD. I've had the same errors with multiple 5.04 and 5.10 installation attempts. First, I initiallized the HD with Apple's Disk Tools, and once in the Ubuntu partitioner, I found that the disk now had 4 small Mac partitions and a Patch partition, as well as the 8.6 GB and 21.5 GB HFS+ partitions I set up. In Ubuntu, I aded a 15 GB FAT32 partition, and let the auto-partition set up 1.0 MB boot and 113.8 GB ext3 root partitions. 

The rest of the CD-based install worked fine, but upon reboot to get the HD to finish the job, I'm left with the boot prompt responding to my request for Linux with:

Please wait, loading kernel...
/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@0:10,/boot/vmlinux: Input/output error

I've searched the forums and on Google, but still can't find any hints on how to proceed. Also checked out the O'Reilly Linux Nutshell book from the library. (Did learn about the "single" tag, but still not helpful.) Incidentally, prior Live CD runs were successful when the HD was not touched.

Well, any thoughts out there? Many thanks if you've got an idea!

- Marc

---

### Post by Oggball on 2006-02-08
I've been reading about your installation dilema in the forums.  Have you solved he problem yet? I have a friend who has a legacy iMac PowerPC G3 233, and we've been thinking of converting it over to Ubuntu primarily so that we could utilize the linux-support of voice-chat in various products.  Mac 8.6 is woefully lacking in voicechat.

Your original post was in Sept'05.  It's now Feb/08/'06...  Just wondering if you had any success with the Ubuntu/iMac installation.

---

### Post by linear on 2006-02-08
There are a few potential quirks, which you can read about in the PPC forum - but yes, you can install and use Ubuntu an an iMac. (As I'm doing right now.)

---

### Post by mcruser on 2006-02-09
Hi, Oggball -

I later got a lot of help from folks when I re-posted on another thread:
[http://ubuntuforums.org/showthread.php?t=70946](http://ubuntuforums.org/showthread.php?t=70946)

Since then, I got Ubuntu up on my B&W G3 and later upgraded to 5.10. It's kinda slow, so I later figured out how to change the window manager, which helped slightly. I'm still working on the printer connection, and I've noted that DVD viewing is not quite as good as my OS 9. Still, it seems to work ok, and hopefully will improve further as time permits.

Summarizing from the other thread, the hotplug component of the Linux system is what was locking my system up the most. With help from others, we found the offending configuration line, edited it out, and it seems to work better.

Good luck!

---

