---
title: "Getting the Live CD to Boot"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by oldnumber11 on 2006-05-15
Here's the scoop. My computer doesn't seem to recognize the live CD at Boot-up. When i burned the .iso onto the CD, my cd software would not recognize the full file name (ubuntu-5.10-live-i386.iso). It was shortened to ubuntu_1. Is this a problem. When I used mdsummer to check the sums, the burned .iso did not match the original .iso. Any ideas?

---

### Post by MaximB on 2006-05-15
try to run this cd from windows -
does it "autorun" ?
try to configer the boot seqance in the bios so it would boot from the cd first.

---

### Post by Jagot on 2006-05-15
Also, you did burn the iso as a disk image and not just as a data CD?

---

### Post by 5-HT on 2006-05-15
[quote=oldnumber11] When I used mdsummer to check the sums, the burned .iso did not match the original .iso. Any ideas?[/quote] 
As Jagot mentioned, it is important to burn the iso as a disk image, not as a data CD. 
Once burned, you should see many files and directories on the disc, not just the iso file.

At the risk of stating the obvious, did the md5 digest of the iso you downloaded match that posted on the download website?

If it was burned as a disk image and the md5 digest of the burned CD (recreated as a disk image) does not match that of the original iso, that could very well be the problem.

If you don't have an easy way of recreating the iso from the burned CD, there are message digests for every file in the iso that you can check. 
It is very important that they match or else the CD will be corrupt (and may or may not boot).

Burning at a slower speed may help (<= 4x) prevent against creating corrupt CDs.

Hope that helps.

---

### Post by r4ik on 2006-05-15
Download anotherone,

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Burn it as image bin/cue

You could try this software.

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm) (if you got Xp)

Or use a Nero trial version.

[http://www.nero.com/nero6/eng/Trial_Versions.html](http://www.nero.com/nero6/eng/Trial_Versions.html)

Set your bootorder to  boot from cd.

If i stated the obvious please ignore.

Good luck !

You could paint a house while i am posting nevermind.

---

### Post by oldnumber11 on 2006-05-15
I used a new cd burning software, Deepburner, and I am up and running. now I need to take a good look at ubuntu. :)

---

