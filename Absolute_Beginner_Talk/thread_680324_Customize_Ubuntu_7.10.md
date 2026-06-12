---
title: "Customize Ubuntu 7.10"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by bprof on 2008-01-27
Hi,

I'm trying to customize Ubuntu 7.10 to include the applications I use the most on a LiveCD. So far I've tried reconstructor and remastersys, reconstructor was really bad, at least for me, remastersys seemed to work as I want but when I do a test of the cd for errors I get three errors, and I cant use the sudo command with the default password (or any other password).

Do you guys know a way to do customization for Ubuntu, other than these two? Or at least easy way to do it, error free?

Thank you,

---

### Post by ctswhole on 2008-01-27
I'd be interested in any answers as well.

I used remastersys once, and it didn't turn out too well.  Basically what I did was do a fresh install of Linux Mint on my laptop, and then fix the Broadcom wireless issue.  After that I used remastersys to make a live cd, and that part worked great.  After booting with the cd, wireless was enabled out of the box, it was great.  But when clicking on the install icon, it was asking for a password, and no matter what password I entered, it was no good.  Would have liked to known what went wrong there.....

---

### Post by bprof on 2008-01-27
I solved it, the solution was upgrading remastersys to 2.0.2. Try ctswhole, it should work.

---

### Post by ctswhole on 2008-01-27
I'll give it a shot and see what happens.  I won't need to try this for a little while, at least until I get done with my Linux From Scratch attempt.  Thanks for the info

---

### Post by bprof on 2008-01-28
No problem, and good luck.

---

### Post by Pelham123 on 2008-01-28
This link maybe of use if you want to do it 'manually' ;)

[https://help.ubuntu.com/community/LiveCDCustomization?action=show&redirect=LiveCDCustomization%2F7.10](https://help.ubuntu.com/community/LiveCDCustomization?action=show&redirect=LiveCDCustomization%2F7.10)

Have used it in the past for 6.06 and it worked a treat

---

### Post by goodrench on 2008-01-30
I have been playing with remastersys and I had the same password problem but later found out that the password for the default user is just blank.
I also discovered that when I logged out and back in with the username and password of my physical system I was looking at my original desktop with all of my programs and settings, including the ones that I had compiled from source.
This program is great.
I am having one problem though.
On my work pc I cannot get an iso file larger than 10 M.
I have tried cleaning my cached downloads.
Every time I try it takes a couple of hours to complete but it only makes an iso 10 megabytes in size.
I have looked at the error log and it says that the .squashfs file is too big.
I looked at the file it was referring to and it was 5.5 gigs in size.
I am not sure what the problem is or how to fix it.
Has anyone else had this problem?

---

