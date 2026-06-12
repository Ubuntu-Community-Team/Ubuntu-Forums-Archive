---
title: "Hard Drive Noise"
date: 2008-02-28
forum: Apple Intel Users
---

### Post by wiz561 on 2008-02-28
Hi!

I've just installed Ubuntu on my SantaRosa Mac Book Pro yesterday.  It seems like after I installed everything and followed the instructions on the ubuntu wiki ([https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)), my hard drive makes a strange noise every couple of seconds.  It never made the noise before, and it doesn't make it when I'm in booted in OS X.  It sort of sounds like the hard drive is dying, but I see absolutely nothing in any of the logs.  It also sounds like a little buzz.  Also, works flawlessly in Mac OS, which makes me think that it's something related to a driver in Ubuntu. 

Has anybody else had a similar experience?  

Thanks!

---

### Post by Rog-Mahal on 2008-02-28
You might want to check out [this link]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") regarding a potentially serious problem with Ubuntu's default laptop power management. I believe you will find a work-around for it as well. Make sure to read the bug symptoms to make sure you're having the same problem.

---

### Post by wiz561 on 2008-02-28
Thank you so much for the link.  It's strange because it didn't seem to happen until I went through the power stuff in the wiki page.  Maybe I'll try to go through it again and see what happens.

You're right though, I will have to go through the bug page and see if it's related.  I'm currently running a surface scan of the drive to see if it returns anything.  But I bet it's somehow related to the power management profile that I put on ubuntu.

Thanks for the link!

---

### Post by cyberdork33 on 2008-02-28
Yea if you messed with power management, i can almost guarantee that was it.

---

### Post by wiz561 on 2008-02-29
An interesting development....

I undid all the power management stuff I screwed around with, and it was still making the noise.  So, I thought, hey, I just installed it and didn't do much, so why not just wipe it and start over again.  I boot up off the live cd installation disk, and while I was going through the installer steps, it started making that noise again.

So, it makes me wonder if the noise is just suppose to happen, if it's something messed up with my computer, or if it's something ubuntu related...

Thanks!

---

### Post by cyberdork33 on 2008-02-29
> **wiz561 said:**
> An interesting development....

I undid all the power management stuff I screwed around with, and it was still making the noise.  So, I thought, hey, I just installed it and didn't do much, so why not just wipe it and start over again.  I boot up off the live cd installation disk, and while I was going through the installer steps, it started making that noise again.

So, it makes me wonder if the noise is just suppose to happen, if it's something messed up with my computer, or if it's something ubuntu related...

Thanks!Well, even in the livecd, it is ubuntu. If you _never_ get the issue in OSX, then I would say it is definitely something in ubuntu.

---

### Post by wiz561 on 2008-02-29
OK, I'm stupid...lol....

I booted up in Ubuntu and it seems like the problem is now gone after I removed all the power changes I did.  I don't know why it was doing it on the livecd...who knows.

Anyways, I am pretty sure now that it's related to the power management changes I made.  I looked at the power management URL link and saw to run smartctl to test for it.  After reading the post a bit, I noticed that in order to use the 'fix', change the hdparm settings.  I didn't do any of this, but check this out.  This is the link to the instructions I was following...

[https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

One of the sections is...

Added a control of the hard drive power saving mode depending on wether the laptop is plugged in or not.

And furthermore, in the script that I was using, there is a 'hdparm' setting in there.

                hdparm -B 200 /dev/sda  (or set it to 50)

So, I'm pretty sure that the reason my drive was possessed was because of this setting.  Hope that this can help somebody else out.

By the way, my drive is a...

Device Model:     FUJITSU MHW2160BHPL


Thanks again for all of your help!!!!

---

