---
title: "Computer restarted in the midst of installation...is my HD fried?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by rexregum on 2007-10-08
While installing Feisty,  I kept getting messages about *.deb files being corrupt.  It also mentioned being unable to download them.

Download them?  Wasn't it reading them off the alt-CD? :confused:

Well, after the third red message came up, I restarted.  And now, my computer is not booting at all.

It performs a mem check, and I press DEL to enter my CMOS.

Here, I ensure that CD-ROM is at the top of the boot list.  It's the first device to check.

But now, despite a CD (Ubuntu, XP, whatever) being present, it doesn't check the drive.

It gets to the screen where it would normally say "Checking Atapi for bootable CD", but it just hangs.

- - -

I tried making my HD the boot option, but no avail.

- - -

Is there some way I can use a floppy disk to intall a basic system, from which I can run a CD again?

Thanks in advance.

---

### Post by dasunst3r on 2007-10-08
Your HD is not fried by any means.  However, you should burn another LiveCD because that CD is definitely no good.  For this next go-around, here are a few tips:
1. Before burning, perform a MD5 sum check on the .iso file you download
2. Before installing, run the media check routine available during boot

---

### Post by expatCM on 2007-10-08
You say ...

> But now, despite a CD (Ubuntu, XP, whatever) being present, it doesn't check the drive.

Whilst you would be wise to burn a fresh Ubuntu CD for installation this may not be your only problem.   It sounds a little like you could have a problem with the CD drive itself.

Have you considered cleaning the CD drive lens just in case it is a dirty lens causing you problems?  You may also want to check that the ribbon cable (at the rear of the drive) is tightly seated.

You do not mention whether there is any evidence of activity (such as the read light) appearing on the CD drive as you power on ...

---

