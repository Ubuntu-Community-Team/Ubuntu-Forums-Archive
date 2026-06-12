---
title: "Live CD on Dell e1505 Wireless not working"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by robgrant on 2007-02-03
I'd like to try Unbuntu from the live cd without installing first.

I downloaded the iso and make a CD, it boots into Ubuntu--but no wireless connection. Two questions, (well actually four, but who's counting?):

1. Is there a way to get this to work after booting into unbuntu? How?

2. Is there a way to recompile the cd so this will work everytime I put the disk it? How?

Thanks people

:lolflag:

---

### Post by Slychilde on 2007-02-03
> 1. Is there a way to get this to work after booting into unbuntu? How?

Yes, there is, but the only way I know of requires you to install Ubuntu.  This will work if your laptop is using the broadcom 1390 adapter, which it most likely is.  Follow [these]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=broadcom+inspiron") instructions and it should work.

> 2. Is there a way to recompile the cd so this will work everytime I put the disk it? How?

I have no clue about that one.  I doubt it, but you never know. 

I hope the link helps.  I was rather reticent to wipe my laptop and try Ubuntu on it, but it was rather painless.  Then again this is the second pc I've put Ubuntu on, so that helped a ton.

---

### Post by robgrant on 2007-02-03
OK, maybe I didn't make myself clear.

The question was whether there was a way to boot off of the CD (use the CD as a Live CD) and NOT install and have wireless networking work.  What is the sense of a LIVE CD if half of the hardware is not going to work unless you install?

The second part of the question was whether the CD could be recompiled to automatically boot with the hardware working.

---

### Post by Slychilde on 2007-02-04
> OK, maybe I didn't make myself clear.

The question was whether there was a way to boot off of the CD (use the CD as a Live CD) and NOT install and have wireless networking work. What is the sense of a LIVE CD if half of the hardware is not going to work unless you install?

No, that was the answer.  You can not do this.  When you compile the wifi drivers in ndiswrapper, it requires a restart.  Live CD's do not use your hard drive, they load to your ram, which when RAM loses it's charge, all information is lost - aka all the changes you made.

The advantages of having a live CD are that you can use them in an emergency to repair a broken OS (hopefully); you can test out the OS without losing your current one; you can see if all/most of the drivers are installed/configured automatically; and you don't  need a hard drive.  They're great for checking out different distros.  You'd be amazed how different each flavor of linux is.

Of course they're not going to auto-detect every configuration known to man.  Many companies refuse to support linux and it takes FREE contributions of people's time to reverse engineer most of this stuff.  Does windows have all the drivers installed when it's first installed? Not by a long shot.  So, why should you expect a live CD to have every driver out there pre-installed?  Microsoft doesn't even have a live CD; it's all or nothing.

Play with the Live CD and see if you like Ubuntu.  Try and customize stuff and mess around a bit.  You can't break anything since all the changes are erased on restart.  If you like it, take the plunge and install it; if you don't, then don't.  Welcome to the power of choice. :)

---

### Post by robgrant on 2007-02-04
OK, that was my question.

So there is NO way to do this.

Thank you, I'll move on.

---

### Post by st33med on 2007-02-04
Yes there is a way to do this!!!!!!! Don't leave!

There is a HOWTO for your wireless card, [click here]("http://www.ubuntuforums.org/showthread.php?t=297092") for the solution

---

### Post by robgrant on 2007-05-09
OK, I'm back.

I read through your instructions, but still don't see how this will work off of the Live CD.

I guess what I'm looking to do is remaster the Live CD so that it at least works with the standard wireless in the Dell e1505 laptop.  I DO NOT, I REPEAT, I DO NOT WANT TO INSTALL UBUNTU just yet.

If there is no way to do this, just say so.

Thanks
:guitar:

---

