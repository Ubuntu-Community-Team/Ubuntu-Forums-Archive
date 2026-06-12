---
title: "System freezes when installing Ubuntu v12.04 on MBP 5,3"
date: 2014-09-11
forum: Apple Hardware Users
---

### Post by dcnicholls on 2014-09-11
When I try to install v 12.04 on my old (5,3) MBP, (provided I change 'quiet splash' to 'no splash' in the script), the script runs for a bit and then hangs at the line:

[58940431] fb: conflicting fb hw usage nouveaufb vs EFI VGA - removing generic driver

Is there a way around this?

DN

(I can get the Try Ubuntu process to boot to completion.)

---

### Post by dcnicholls on 2014-09-11
Solved: I changed the 'quiet splash' to 'nomodeset' in the Grub script (via 'e' from the boot menu with 'install Ubuntu' selected), then pressed F10, and the installation proceeded correctly.  Using 'no splash' appears not to work in this context.

Now all I need to do is to work out how to configure the partitions....

---

### Post by Bucky Ball on 2014-09-11
Not a Mac user, but at the very least you will need:

/ = where the OS goes, and;
/swap = a swap partition, 2Gb fine. 

Some people add a /home partition for personal data. If you do this, make the / partition around 20-25Gb. You probably won't need that much but can shrink later if required. If you don't create a /home partition, your /home will be a directory inside / and your personal directories and data, e.g. Documents, Pictures, Music, etc., will be inside /. In this case, make / big!

During the install, if you choose 'Something Else' you can manually partition. The mount points /, /home, /swap and many others are available by default to select. Good luck.

Anyhow, off-topic on my part. If you'd like more help with that, post a new thread and the link here. ;)

---

### Post by dcnicholls on 2014-09-11
Thanks.  I got it working, though I'm not entirely sure I did it the right way. But working is working.  Originally I had the rEFInd boot manager , but it seemed to be in  conflict with the grub system.  I removed rEFInd and installed the older rEFIt system, and (possibly because of the sequence of installing), I can now boot directly to the Mac, or, booting with the option/alt key, it boots to rEFIt, and I can select Ubuntu.  That takes me to the grub screen, which is unnecessary, but one more click and Ubuntu boots.  I set 40Gb disk space for Ubuntu and 10Gb for swap.

I only need Ubuntu at present for one project (scientific), so no photos or music.  It is a very nice OS.

Ideally I'd like to have rEFIt open on boot, and then boot directly to either Mac OS X or Ubuntu, with no intermediate steps.  But I don't yet know enough about the booting mechanism(s) to do this.  Any tips from others who've done this would be much appreciated.

---

### Post by Bucky Ball on 2014-09-11
Great news you got it all working, but a 10Gb swap is way overkill unless you have 10Gb or more RAM and hibernate regularly. As I say, 2Gb is all that is required.

> **dcnicholls said:**
> 

Ideally I'd like to have rEFIt open on boot, and then boot directly to either Mac OS X or Ubuntu, with no intermediate steps.  But I don't yet know enough about the booting mechanism(s) to do this.  Any tips from others who've done this would be much appreciated.

You might like to post a new thread regarding this to improve your chances of help as it is another support question and not related to the title of this thread. 

Good luck.

---

### Post by dcnicholls on 2014-09-11
Thanks.  I'll open a new thread on this last point.

---

