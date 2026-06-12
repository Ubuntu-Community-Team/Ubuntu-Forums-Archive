---
title: "Hung up in install"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Jeff Green on 2007-01-16
Over the past couple of weeks I've been trying different things and searching the forums and other online documentation, but haven't found a solution.

My company is ready to donate some older Dell PCs to a local crisis center, but the hard drives must be wiped clean. I was hoping Linux would make a stable, low-maintenance system for their use as walk-up computers. They will use them mainly for email.

To test, I ran the install on a Dell GX280 (P4, 256 MB RAM), and it worked perfectly. But when I tried installing on both an Optiplex (P3, 128 MB RAM) and a Precision 210 (P3, 1 GB), the PCs we can donate, I couldn't get it to work. I also tried Xubuntu on the Optiplex, but had the same trouble.

When I boot up with the Ubuntu CD, I get the splash screen and begin the install. After a few minutes though, I get the message 188.110413 Buffer I/O error on device hdc, logical block 1. This message repeats itself numerous times, with different numbers. Finally, I get the message:
BusyBox v1.1.3(Debian 1:1.1.3-2ubuntu 3) Built-in shell(ash)
Enter help for list of built-in commands
/bin/sh: can't access tty: job control turned off (initramfs)

I've tried different hard drives and CD ROMs and CDs.

Any help would be much appreciated!

Jeff

---

### Post by bunabattoir on 2007-01-16
This sounds like a bad CD. I would check the md5sum of the .iso you burned. YMMV.

---

### Post by Jeff Green on 2007-01-16
How do I do that? I used the same CD that worked on the successful GX280 install.

---

### Post by bunabattoir on 2007-01-16
> **Jeff Green said:**
> How do I do that? I used the same CD that worked on the successful GX280 install.

Did you burn this CD from a d/l'd .iso? If so, at that same website will be an md5sum file associated to that iso. You will then have to run the md5sum utility using that file and the iso as parameters (the md5sum util is standard on (essentially) all linux distros; a Win32 version can be found [here]("http://unxutils.sourceforge.net/").)

It is possible that the CD reader is the culprit, though this is less likely.

---

### Post by Jeff Green on 2007-01-17
bunabattoir, thanks for your help. I finally figured it out based on the clue you gave. I had tried other CD drives in the PC that wouldn't load, including the drive from the PC that loaded successfully, but it didn't work. So yesterday I stuck in a drive identical to the one used to burn the ISO, and it worked perfectly.

Thanks again,
Jeff

---

