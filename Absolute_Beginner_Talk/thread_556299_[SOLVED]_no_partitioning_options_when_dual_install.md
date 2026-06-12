---
title: "[SOLVED] no partitioning options when dual installing!"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by tommason on 2007-09-21
Hi,

I am trying to dual install Ubuntu onto my desktop which already has vista installed on it.

I have left a good size (25GB) of unpartitioned space on my hard drive and commenced the installation, filled out all the keyboard info etc etc, chose manual in the partition options. 
This then left me with no options whatsoever..... :(

any ideas?

Cheers!

Tom

---

### Post by wjp.reg on 2007-09-21
There are numerous tuorials and guides for dual-booting vista and ubuntu..

[Here's one you could have googled.]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

cheers, and good luck!

---

### Post by tommason on 2007-09-21
that's the one I've been using.....as i said, i boot through the live cd, input all my info (location/keyboard language etc) i then get to the partitioner which ONLY gives me the option of a manual partition setup. I select this, which leads me to the next page, which has no options :( I can't select a partition on which to install.

Shall i setup a partition within windows and re-run the cd?

---

### Post by overdrank on 2007-09-21
> **tommason said:**
> that's the one I've been using.....as i said, i boot through the live cd, input all my info (location/keyboard language etc) i then get to the partitioner which ONLY gives me the option of a manual partition setup. I select this, which leads me to the next page, which has no options :( I can't select a partition on which to install.

Shall i setup a partition within windows and re-run the cd?

Just to double check, is the drive mounted on the desktop? Some times the live cd will mount the drive with the other OS on it therefore you can not partition that drive.

---

### Post by tommason on 2007-09-21
> **overdrank said:**
> Just to double check, is the drive mounted on the desktop? Some times the live cd will mount the drive with the other OS on it therefore you can not partition that drive.

I'm not sure :s how would i find this out :)

---

### Post by overdrank on 2007-09-21
> **tommason said:**
> I'm not sure :s how would i find this out :)

If the drive is mounted it will show on the desktop of the live cd or in the places,home  you can right click on it and select unmount.

---

### Post by tommason on 2007-09-21
> **overdrank said:**
> If the drive is mounted it will show on the desktop of the live cd or in the places,home  you can right click on it and select unmount.

No, there's no other os mounted on the desktop or in places.... I think the issue may be that it can't see my hard drives, they are connected via SATA....

---

### Post by overdrank on 2007-09-21
> **tommason said:**
> No, there's no other os mounted on the desktop or in places.... I think the issue may be that it can't see my hard drives, they are connected via SATA....

Ok I am using sata drives and have no problem. Look under system, administration, Gparted and see if it is seen there.

---

### Post by tommason on 2007-09-21
just waiting for gparted..

meanwhile, on booting from the live cd there were some messages which I'm not sure have relevance or not:
137.163589 ata6.0 failed to set xfermode (err_mask=0x40)
and two more similar....

I also just got (for no apparent reason, i wasn't doing anything):
 cannot mount volume
mount: block device /dev/fdo is write protected, mounting read only mount: /dev/fdo can't read superblock

anything in them?

---

### Post by tommason on 2007-09-21
> **overdrank said:**
> Ok I am using sata drives and have no problem. Look under system, administration, Gparted and see if it is seen there.

gparted shows nothing, all options are greyed out apart from refresh and help....

---

### Post by overdrank on 2007-09-21
> **tommason said:**
> just waiting for gparted..

meanwhile, on booting from the live cd there were some messages which I'm not sure have relevance or not:
137.163589 ata6.0 failed to set xfermode (err_mask=0x40)
and two more similar....

I also just got (for no apparent reason, i wasn't doing anything):
 cannot mount volume
mount: block device /dev/fdo is write protected, mounting read only mount: /dev/fdo can't read superblock

anything in them?

Yes those errors could stop it form detecting the drive. try and defrag the windows partition.

---

### Post by meindian523 on 2007-09-21
But isn't /dev/fd0 for the floppy rather than the HDD??

---

### Post by tommason on 2007-09-21
> **overdrank said:**
> Yes those errors could stop it form detecting the drive. try and defrag the windows partition.

ok, will do!....i don't need to make a separate partition in windows partition maker? would that help at all?

---

### Post by tommason on 2007-09-21
superb! - didn't thin kthat a simple defrag would work, but that has sorted it...installing as we speak :D
thanks a lot for your help
Tom

---

### Post by overdrank on 2007-09-21
> **tommason said:**
> superb! - didn't thin kthat a simple defrag would work, but that has sorted it...installing as we speak :D
thanks a lot for your help
Tom

Great glad to hear, Could you mark as solved thanks! Good luck and enjoy! 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by tommason on 2007-09-21
ok - i f i knew how to mark as solved i would.. :)

I am getting more issues however, which i'll put on another post....

---

### Post by tommason on 2007-09-21
got it

---

