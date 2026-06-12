---
title: "messed up reinstall and partition of ubuntu"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by mg620 on 2006-10-14
I've been using ubuntu 6.06 for 2 weeks.  Everything was great until my screen resolution suddenly dropped to 640x480.  I tried to follow instructions to resolve it through Xorg, but pretty much screwed it up so badly my computer wouldn't start.

I figured I'd just reinstall ubuntu.  When choosing partition size, I chose 100% of the partition that was already ubuntu (the screwed up one, which was 15 GB).  When all was said and done, however, I now have ubuntu on a 2.3 GB partition and a 13.7 GB partition I can't use.  And grub shows 2 extra ubuntu choices now.  So instead of wiping the ubuntu partition, I just added another smaller one.

What I need to know is how to truly wipe my ubuntu partition(s) and reinstall ubuntu so that I have one ubuntu partition and one windows xp partition.  (I did search the forums without success.)  Also, can I edit the boot loader so that I go back to the original number of choices without the duplicates?

---

### Post by ReaderRat on 2006-10-14
Are you dual-booting with Windoze?
These may help:
Partitioning - General
          [http://www.ubuntuforums.org/showthread.php?t=275454](http://www.ubuntuforums.org/showthread.php?t=275454)
Partitioning - Windows & Linux
          [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
ReInstalling Windows & Recovering Ubuntu          [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by mg620 on 2006-10-14
Yes, I am dual-booting with "Windoze."  For now, anyway.  I will check your links, thanks.

---

### Post by deadgobby on 2006-10-14
1st you must boot windows and then other o/s secound. MS does not play nice with other O/S.
Here is video for you to whatch. It may be for breezy, but the same concept.
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

GObby

---

### Post by mg620 on 2006-10-14
I think I need to clarify...windows is working fine, ubuntu is working fine, except that it's now on a tiny partition and there is an extra partition in there that I can't use or "mount."  I just want to wipe everything that is **not **Windows and start fresh.  Thanks.

---

### Post by navneeth on 2006-10-14
I was in almost the exact position when I started out, except that it was Kubuntu which had a messed up resolution. :D 

Thankfully, I didn't have to go through the partioning part, since I had/have installed Kubuntu/Ubuntu on a seperate hard-drive, which does not contain Windows' C: drive. So I made some space using the [url="http://gparted.sourceforge.net/livecd.php"
]Gparted LiveCD[/url], and then let Ubuntu install itself in the free space.

---

### Post by oliverb on 2006-10-14
Regarding the partitioning problem: It looks like you just need to use the installer but tell it you want to set the partitions manually. Then you can delete the existing linux partitions to create a hole, and create a new partition in the hole.

---

### Post by mg620 on 2006-10-14
Thanks, everyone.  Kudos to navneeth and oliverb.  You were both right on (Gparted is the partitioner on the install cd.)  I ended up downloading the Gparted liveCD and using that, since it had some basic instructions.  Once I read the instructions, how to manually partition become very clear and easy.  The basic book I am using as a tutorial does not describe manual partitioning; too bad.

Now if only I could get my modem and printer to work... ;)

---

### Post by Sef on 2006-10-14
> Now if only I could get my modem and printer to work..

Post those problems in two different threads, please.

---

