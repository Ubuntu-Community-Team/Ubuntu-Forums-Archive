---
title: "Problems with harddrive access"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by sn4cks on 2007-07-03
As of yesterday, I installed Ubuntu with the plan to keep my installation of Windows 2000 and then just dual boot. I went through the setup with no problems, I've had experience with partitioning individual drives before, so it seemed like everything was working just fine.

I have 2 HD's, 1x 40GB, which is the one that Windows is on, and 1x 250GB. I had both drives set up as a C: and G: drive, C: being the 40GB and G: being the 250GB. G:'s label was "ROBOT SLAVE". So anyway, because of the fact that Windows 2000 can't handle all 250GB of the drive, I only had half of that space used in Windows, aprox 118GB. Since I installed linux, I just created partitions out of the remaining space and it worked out great. Plus, when I finally finished installing I was happy to see that it had auto-mounted that drive and put a link on my desktop, since that drive has all my music and movies on it.

This morning, I re-booted my computer, as there was some things I wanted to do in Windows. I selected Windows 2000 from the boot menu and it started up just fine. Once it had finished loading and I logged in, I opened my computer and noticed that G:'s volume label had disappeared. I double clicked on the drive and it told me that it needed to be formatted.
I wondered "Hmm, that sucks. I wonder if maybe it's because I didn't unmount it before I exited out of Ubuntu...", so, I restarted into Ubuntu and tried unmounting. It won't let me.

So basically the issue is this: Why can't I use that drive under windows anymore? I didn't change anything on that drive besides created 2 new partitions (swap & primary) during my Ubuntu install. Did I mess something up? Is there a way to fix it?

Sorry this is so long, but I just wanted to explain everything so things would be more clear.

---

### Post by blastus on 2007-07-03
[quote=]So anyway, because of the fact that Windows 2000 can't handle all 250GB of the drive[/quote]

Windows 2000 can certainly handle a 200GB drive no?.

[quote=sn4cks]I wonder if maybe it's because I didn't unmount it before I exited out of Ubuntu.[/quote]

No. What you mount/unmount in Linux does not affect anything Windows sees. However, if you repartition a drive or reformat a partition, it will affect what Windows sees.

[quote=sn4cks]Why can't I use that drive under windows anymore?[/quote]

I don't know. I forget what the tool is, but you can go into Administrative Tools and examine all the drives and what drive letter Windows has mounted each to. From there you can unmount and re-assign the drive letters. If you repartitioned that 250GB drive in any way, you should unmount and re-assign all the drive letters that previously belonged to that drive.

---

### Post by sn4cks on 2007-07-03
> Windows 2000 can certainly handle a 200GB drive no?.

according to my room-mate, it only's handles up to a total of aprox 200GB, so since I already had a 40GB drive I couldn't utilize the entire thing. something about windows 2000 not having the correct filesystem support? I don't remember everything he told me, but I do remembering him getting frustrated when explaining it and saying "Just do what I say."

Haha, he's kind of a jerk.

> No. What you mount/unmount in Linux does not affect anything Windows sees. However, if you repartition a drive or reformat a partition, it will affect what Windows sees.


Alright, thanks a bunch for clearing that up for me.


> I don't know. I forget what the tool is, but you can go into Administrative Tools and examine all the drives and what drive letter Windows has mounted each to. From there you can unmount and re-assign the drive letters. If you repartitioned that 250GB drive in any way, you should unmount and re-assign all the drive letters that previously belonged to that drive.

I actually *think* I remember how to do that, so thanks a bunch!



So basically, what you're saying is the reason it's probably not working now is because I re-partioned the drive and I hopefully just need to re-configure the way that windows is seeing/mounting the drive. Right?

Thanks for all your help!

---

### Post by blastus on 2007-07-04
[quote=sn4cks]So basically, what you're saying is the reason it's probably not working now is because I re-partioned the drive and I hopefully just need to re-configure the way that windows is seeing/mounting the drive. Right?[/quote]

It's quite possible.

---

### Post by captainwitherspoon on 2007-08-15
I'm having a similar problem, how do you change the way windows sees the drive?

---

### Post by Hobo Joe on 2007-08-15
This has happened to me, are you using the Windows ext3 driver?

Usually a reboot fixed it.

---

### Post by captainwitherspoon on 2007-08-15
To be honest I don't know. Win2k can't see my ubuntu drive, I don't know why..

---

### Post by Hobo Joe on 2007-08-15
> **captainwitherspoon said:**
> To be honest I don't know. Win2k can't see my ubuntu drive, I don't know why..

Try [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by captainwitherspoon on 2007-08-16
fs-driver didn't work for me. It implies my drive isn't .ext2[?]
I was working on this before and I remember using the fdisk-l command, when I type that right now nothing is displayed, weird. Any ideas?

---

### Post by captainwitherspoon on 2007-08-30
Hi, I know it's been a while and it's probably too late to help but I was using this thread and finally figured this out. win2k, in all of it's glory, can only read drives up to 137gb without sp4 and some registry tweaking. try this [http://support.microsoft.com/kb/305098/en-us](http://support.microsoft.com/kb/305098/en-us) *then* fs-driver will work.

---

### Post by radioraheem8 on 2007-08-30
Yeah, I'm pretty sure W2K does not support hard drives of that size.  I think mine cut off at 137 gigs.  

Anyways, I'm having a similar problem.  I have a small 20 gig'er for Linux, but a 137 gig for W2K storage (no dual boot system, I just plugged it in as a slave).  Ubuntu recognized the drive, so my stuff was accessible.  However, I recently had video driver problems, and now I can't seem to see the HD anymore.  

fdisk -l gave me this:

Disk /dev/sda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2382    19133383+  83  Linux
/dev/sda2            2383        2491      875542+   5  Extended
/dev/sda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/sdb2           16710       24792    64926697+   f  W95 Ext'd (LBA)
/dev/sdb5           16710       24792    64926666    7  HPFS/NTFS

Am I missing something really obvious?  It seems to see the drive in that command...

---

### Post by radioraheem8 on 2007-08-30
Never mind.  I'm an idiot; I was still in recovery mode!

---

