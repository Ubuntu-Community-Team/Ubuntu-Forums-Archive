---
title: "Install Ubuntu on a HD from the desktop?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Ocarina654 on 2007-11-13
So its been a bit of a bumpy ride trying to get everything working so far but I am determined to get this to work.
So here's my question.  Actually here's the lead up to my question, the real question is at the end.  I figure that at least some of this info might help.

I'm running Ubuntu off of a USB Hard Drive connected to my computer.  My internal HDD is formatted to ext3.

GParted sees it (that's how I formatted it) and running "sudo fdisk /dev/sda -l" sees it and gives me this:
```
 Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003ed4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   83  Linux 
```

Everything seems to be in order.
However, everything seemed to be in order last time I tired to install (7.10 Alternate CD) and yet the install didn't see the drive.  This could have been for a number of reasons, hopefully all of which I've addressed (if you'd like information I'll share the saga!).

Now, I'm a little afraid of restarting the computer and trying to install from the alternate CD because this hasn't worked in the past with this drive (however it did work for the external, which as previously mentioned, I'm running from now, so, again, it was likely my drive).  I realize this might be a somewhat silly/irrational fear, but I really want this to work with as few hiccups as possible.

So, my real question is this:
Is there a way to Install Ubuntu to a hard drive while running the Ubuntu desktop from a separate hard drive?
If not, just some reassurances that I'll figure this out eventually would be great! :mrgreen:

If any further information is necessary to get this to work I'd be happy to share.

---

### Post by MaximusTG on 2007-11-13
Well, it is even possible to make a complete copy of your current installation on your USB harddrive  to your internal one.. 
But may I ask why you don't just use the live-cd to install Ubuntu? That way you can easily check whether or not your harddrive is detected. 
You should probably just try to install it to the internal drive with the install cd you have, but unplug your USB one, so then you have nothing to lose right?

If you want to know how to copy your install to the internal drive, just let me know. It involves booting of a live cd, mounting both your internal and external drive, doing a copy, and finally editing your /etc/fstab and install grub.

---

### Post by bulldog on 2007-11-13
I can't think of a reason why you should want to do that.

Anyway, to install ubuntu you have to boot from the alternate cd,and I think you can't manage that,running an OS.

But maybe I'm wrong and you should wait for somebody who has tried it.

---

### Post by Duck2006 on 2007-11-13
Some where in these forms there is a how to, to do just that can't think of what it was called sorry.

---

### Post by Ocarina654 on 2007-11-13
Well, I don't HAVE a 7.10 Live CD and the 7.04 Live CD I do have doesn't support my hardware (kernal issues, not a problem for me at this point, I just don't have the 7.10 Live).
I could always download and burn the ISO from the desktop I'm running now or my other (Mac) computer, but that's just MORE things that I'll have to do and it'll take MORE time to get it done, that's why I wondered if there was a way to do it from here.  It would be, hopefully, quick and easy.

Duck2006: Thanks for trying to remember though.  If it dawns on you one day I'd still be interested to hear about it.  In my searches I couldn't find anything, so yeah... thanks anyway

Also, Bulldog, correct me if I'm wrong, but you're saying that I "can't" manage to boot an OS?  Is this the way you want to treat new users?  Telling them that I can't run Ubuntu?  Or are you just saying that I "can't" boot from a CD?
Either way you are 1) Wrong and 2) Being quite rude to someone who hasn't acted rude, mean, or angry at all.
If it was a typo and you meant "can" then I appologize for taking your typo at face value.

For now I'll try installing from the Alternate CD and will, hopefully, be back on here in a few minutes to let you all know how it went and, if it goes unwell, try to find more help.

---

### Post by Ocarina654 on 2007-11-13
All right, well, I'm not surprised but the Alternate CD Install still isn't seeing my Hard Drive.
Let me remind you that Ubuntu, already installed, DOES see the drive.  I have no idea why the Alternate CD doesn't.
By the way, I ran the checksum and the CD was fine.  It is clean.  My CD drive works otherwise.  The CD worked for a different hard drive.  I know this has something to do with the hard drive itself.  It still makes no sense to me how I can see it from Ubuntu but the Ubuntu CD doesn't....

Anyway, unless anyone comes up with a way to install without having to boot with a CD, I'll be downloading the Live CD and hoping that this one actually works.

Still open to other suggestions, by the way.

Thanks!

---

### Post by bulldog on 2007-11-13
> **Ocarina654 said:**
> Well, I don't HAVE a 7.10 Live CD and the 7.04 Live CD I do have doesn't support my hardware (kernal issues, not a problem for me at this point, I just don't have the 7.10 Live).
I could always download and burn the ISO from the desktop I'm running now or my other (Mac) computer, but that's just MORE things that I'll have to do and it'll take MORE time to get it done, that's why I wondered if there was a way to do it from here.  It would be, hopefully, quick and easy.

Duck2006: Thanks for trying to remember though.  If it dawns on you one day I'd still be interested to hear about it.  In my searches I couldn't find anything, so yeah... thanks anyway

Also, Bulldog, correct me if I'm wrong, but you're saying that I "can't" manage to boot an OS?  Is this the way you want to treat new users?  Telling them that I can't run Ubuntu?  Or are you just saying that I "can't" boot from a CD?
Either way you are 1) Wrong and 2) Being quite rude to someone who hasn't acted rude, mean, or angry at all.
If it was a typo and you meant "can" then I appologize for taking your typo at face value.

For now I'll try installing from the Alternate CD and will, hopefully, be back on here in a few minutes to let you all know how it went and, if it goes unwell, try to find more help.

Hmm not a nice answer,I only ment to say,if your computer is running from an external hdd,you can't boot a cd in the same time.
Why on earth would I keep you away from Ubuntu?
It seems you read my post terrible wrong.
Ofcourse you can run ubuntu and yes you can install ubuntu,but not at the same time.
I won't bother you any longer though.

---

