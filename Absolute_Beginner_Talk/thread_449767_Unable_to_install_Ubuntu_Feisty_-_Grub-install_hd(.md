---
title: "Unable to install Ubuntu Feisty - Grub-install hd(0) fatal error"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by sainib on 2007-05-20
Hi
I downloaded the Ubuntu Feisty and tried to install but when the installation was 94% done and it started configuring GRUB, it gave me an error:
"Executing grub-install (hd0) failed. This is a fatal error."

This is the exact error message shown as a pop up with only two options - Ok and Cancel. So i do not have more details. 

I am trying to set up as multi boot with Windows XP already installed on one of the partitions. I have 3 partitions with XP on one and two for Ubuntu (ext3+swap).

Please help.

---

### Post by Borzo on 2007-05-20
are you installing from the Desktop installation method? or alternate?

---

### Post by sainib on 2007-05-20
I am installing the desktop edition of ubuntu from a CD that i burned after downloading the ISO image from Ubuntu.com. Did i answer your question?

---

### Post by sainib on 2007-05-20
Some more info on this.. 

I tried to run the grub-install directly from terminal and got the following error.

ubuntu@ubuntu:/$ grub-install hd0
mkdir: cannot create directory '/boot/grub': Permission denied. 

So i checked the permissions on directory /boot and found that owner of /boot is the user - root - permissions on /boot is -rw-r--r-- 

I wasnt unable to switch to root user as the passwords i tried failed and i do not remember selecting any password for root user ..

any ideas?

---

### Post by sainib on 2007-05-20
Something more .. 

So I found a posting by Arnieboy about how to switch to root user and that worked so i could su to root and ran the command - grub-install hd0 - again to get the following error. .

root@ubuntu:/# grub-install hd0
Could not find devide for /boot: Not found or not a block device

Googled that and found this posting [http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable)
point #12 - gentoo documentation suggested copying /proc/mounts to /etc/fstab.. Desperate to solve the problem i did that too but no luck.

Then i see OliverP on this page has solved the similar problem by installing lilo.. 
[https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/10556](https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/10556)

Is there any way to get the GRUB working ?

---

### Post by guice on 2007-05-21
Just wanted to make a post pointing out I have the exact same problem. I just tried to install Ubuntu on a new clean parition. It died, with fatal error, with this.

---

### Post by Terl on 2007-05-21
What kind of drives are these?  Would you mind sharing your system specs?

---

### Post by snakedr on 2007-05-21
I have tried to install Ubuntu a couple of times using the liveCD. The install goes fine until the grub install fails. The liveCD will not allow a second try at the grub install if it fails (at least I have been unable to find out how).

I have resorted to using the alternate install CD. When the grub install fails a menu will come up that will allow the grub install a second time. The grub install always succeeds on the second try. I have only tried one distribution that the grub install succeeds on the first try.

---

### Post by guice on 2007-05-21
> **Terl said:**
> What kind of drives are these?  Would you mind sharing your system specs?
Hardware Overview:
  Processor Name:	AMD Athlon(tm) 64 Processor 4000+
  Processor Speed:	2.41 GHz
  Total Number Of Cores:	1
  L2 Cache (per CPU):	1 MB
  CPU Features:	FPU VME DE PSE TSC MSR PAE MCE CX8 APIC SEP MTRR PGE MCA CMOV PAT PSE36 CLFSH MMX FXSR SSE SSE2
  Memory:	1 GB
  Bus Speed:	400 MHz


Installing Ubuntu on a second partition on a standard primary IDE Harddrive.

---

### Post by sainib on 2007-05-21
Snakedr, 

Pardon my ignorance, but can yu tell me how can one get alternate install CD? ( link etc )

Also wanted to ask you if you problem is completely resolved? 

Thanks!

---

### Post by sainib on 2007-05-21
Also, I am going to try to download the Grub 0.97 directly from gnu site and will compile the code and try to run that 
[http://www.gnu.org/software/grub/grub-legacy-download.en.html](http://www.gnu.org/software/grub/grub-legacy-download.en.html)

I will post the results in this post .. meanwhile if anyone has any clue about this error.. please post it here.. Thanks

---

### Post by guice on 2007-05-21
I messed around with the install a couple more times and actually managed to get it installed properly.

Things I did differently this go: I installed Ubuntu on ext2 on /dev/hda2 and created a new /dev/hda3 for swap (previous, I had swap on my scsi0 -- sata -- drive).

Ubuntu managed to install successfully, although GRUB failed to reconginze the OS on /dev/hda1. No worries though as I managed to manually add it to the menu.list and was able to successfully select/boot up into it (in it right now).

So, all golden! All happy now.

---

### Post by virtualpilot88 on 2007-06-02
I have got the exact same problem.

Here is some info about my disks:
Main Drive:
120 GB - 1 Partition - Windows XP (lot's of stuff on it, I don't want to lose)

2nd Hard Drive
30GB 4 Partitions:
1. Windows XP (10 GB)  (main drive had some problems booting it's self so I use this one to boot that - it works).
2. Ubuntu 2 B (9.5 GB)
3. Ubuntu Swab (0.5 GB)
4. Mac OSX86 (Not actually working :???:)

And some info about the rest of my system:
CPU: AMD Sempron 2800 1.8 GHz
RAM: 512 MB
(more on request).

Please give me some help on how to fix this.

Daniel

---

### Post by virtualpilot88 on 2007-06-02
Update: I tried this procedure ( [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) ) and after doing 
```
find /boot/grub/stage1
```

I get the response 
```
File not found
```

---

### Post by tutomlin on 2007-06-03
Hi,

I had a similar problem although my system froze rather than presenting me with an error message.  by brute force (disconnecting various drives and moving hardware around) I finally figured out that the problem was that I had both IDE and SATA drives in the system and was trying to use the IDE as the primary boot drive.  

Windows has to be on the IDE drive to boot properly, and I had the drive in a hotswap style tray so I had just pulled the windows drive and popped in a new drive on IDE1 for Ubuntu.   Apparently Ubuntu has the opposite problem from winXP, and needs to be on the sata drives to install grub properly (at least on my system.)

hope that helps somebody

---

### Post by Ariccanfly on 2007-12-15
wheres the fix? whats the fix? this is not fixed :)

---

### Post by Lorin Ricker on 2007-12-16
I've had exactly the same problem, and posted on this thread --

[http://ubuntuforums.org/showthread.php?t=640913](http://ubuntuforums.org/showthread.php?t=640913)

While responses have been helpful, the advice and my research so far has not resolved my problem either.  Looking around on the Absolute Beginners forum, this grub problem appears to be a major hassle, and appears in several forms.  This seems to be a major bug in Ubuntu -- and noone seems to be able to definitively explain how to fix it (at least, not to us rookies).

See my latest post on the above thread, which responds to dstew's next-step advice.

We need to combine these threads, or at least make sure that responses to either of them get cross-referenced, since we're trying to solve the same problem.

---

### Post by Lorin Ricker on 2007-12-16
Terl asks (post #7 this thread):
> What kind of drives are these? Would you mind sharing your system specs?

For comparison, please also see my #1 post this thread: [Help - Kubuntu 7.10 (Gutsy) fails at "install grub"]("http://ubuntuforums.org/showthread.php?t=640913"), for my own h/w config...

Next, snakedr (#8) recommends:

> 
I have tried to install Ubuntu a couple of times using the liveCD. The install goes fine until the grub install fails. The liveCD will not allow a second try at the grub install if it fails (at least I have been unable to find out how).

I have resorted to using the alternate install CD. When the grub install fails a menu will come up that will allow the grub install a second time. **The grub install always succeeds on the second try**. I have only tried one distribution that the grub install succeeds on the first try.

OK -- anything to move ahead on this.  I've just started the alt-dist download, so stay tooned...

As a newcomer to this Forum and Community, may I ask:  Does this problem, which both sainib and I have independently experienced and reported, constitute something which should be formally bug reported?

It seems, judging from all the grub-related traffic on Abs.Beginners (and elsewhere), that this is a major area of problems for Ubuntu novices (and others?) -- understandable, given that bootstrapping is a tough technical area, and given all the variations of h/w out there -- but this certainly belies the robustness and "ease of installation" which Ubuntu officially promises.  Shouldn't Canonical's developers and support be appraised of this problem and how pervasive it seems to be?  I ask this with respect, intending to help, not just gripe!  :)

---

### Post by Lorin Ricker on 2007-12-17
Hey, sainib!!! -- Check out posting #12 on ["The Other Thread"]("http://ubuntuforums.org/showthread.php?p=3970149&posted=12#post3970149")!  vinay.v's advice looks like it'd solve our shared problem.  I won't be able to reinstall until later this evening, but I'll post my results -- if you beat me to it, post yours as well!  This looks promising.  -- Lorin

---

### Post by Lorin Ricker on 2007-12-19
sainib -- See "the other thread" [Help - Kubuntu 7.10 (Gutsy) fails at "install GRUB"]("http://ubuntuforums.org/showthread.php?p=3977957"), my last post #14.  I finally got a clean install, but not by using any of the [K]Ubuntu Live CDs -- I finally resorted to an install using the Ubuntu v7.10 Alternate Desktop CD, instead.  Full details on that thread/post#14.  Good luck with your PC, and I hope that this helps you too!  :)  -- Lorin

---

