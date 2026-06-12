---
title: "rm -r emergency! [Resolved... mostly]"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2007-04-29
OH CRAP! I can't believe I fell victum to the cliched bad use of running rm -r where I wasn't supposed to. I'll spare you my excuses, I just want to know if there's a hope of recovery for the 60 or so gigs I lost. I've heard of ways to recover data if it isn't written over yet, but I want to be absolutely sure not to accidently write over anything. 

The data is in my home directory on a FAT32 mount. I didn't wipe the whole drive because i killed the process part way through. If I lose everything, the bright side is I can finally convert the drive to ext easily.

Please help!

---

### Post by Soccrmastr on 2007-04-29
wow I cant help you... but geez  thats a lot of stuff... be more careful man!!

---

### Post by aysiu on 2007-04-29
I don't know all the steps to recovery, but start by unmounting the drive **now**.

---

### Post by Ephilei on 2007-04-29
Right: umount -l dev/

---

### Post by psionyk on 2007-04-29
Oh man, that really sucks... I'm not aware of recovery methods either, but my worry about your chances is that you were using your directory in FAT32, which is a horrid filesystem to begin with, let alone the fact that I'm not sure what options Linux doesn't have for FAT that it might have if it was something like Reiser or ext3.  I sincerely hope that you haven't lost all of it permanently...  Good idea to move on to ext3, and if you were using FAT before for Windows compatibility, you can download a filesystem driver for Windows that would allow you to access and read/write to that ext3 partition:

[[COLOR="DarkRed"]_http://www.fs-driver.org/_[/COLOR]]("http://www.fs-driver.org/")

I'd be very curious to hear if there's a way to fix this from people more expert in recovery options.

Good luck with this!

---

### Post by Ephilei on 2007-04-29
I've reconstructed the directory (hopefully only the first level is needed!). All I need to recover are mp3s and m4as; the rest is backed up. I can move the drive to an XP machine if need be, but I'd rather not.

---

### Post by Ephilei on 2007-04-29
Help - please?

---

### Post by aysiu on 2007-04-29
Maybe try [this](http://ubuntuforums.org/showthread.php?t=171100)?

---

### Post by HereInOz on 2007-04-29
If it is a FAT32 partition, you ought to be able to install it in a Windows machine (sorry) and use a data recovery program like FileScavenger or GetDataBack.  Unless the partition has been completely overwritten, you should get some stuff recovered.

My understanding is that rm, like the Windows del command, does not actually remove the files, but merely removes the list of where the files are, if you know what I mean.  The files are still there - you just can't get to them.  One of the two programs listed above may do the job for you.  They only work on FAT32 and NTFS, from memory, so you could be in luck.

---

### Post by jerrylamos on 2007-04-29
"Knoppix Hacks" by Kyle Rankin has a section on recovering deleted files, page 182.  There's lots of cautions since many things you do creates new files which could be using the space that the deleted files are in.  That's why Knoppix is CD Live so you don't accidentally tramp on what you're using.  Maybe you could use Ubuntu CD Live also.  Kyle recommends the utilities "lazarus" and "unrm" from [http://www.porcupine.org/forensics/tct.html](http://www.porcupine.org/forensics/tct.html).

I don't have any experience with this (yet).  Do take a look at the porcupine though, (from another computer or CD Live).

Cheers, Jerry

---

### Post by juantovarm on 2007-04-29
There are plenty of file recovery programs that run under windows. You could try any of them, i have successfully in the past recovered files from formatted disks, takes a bit longer and there's more rubbish but it's pretty easy. I do not remember the name of the program, it was over a year ago, sorry

---

### Post by Ephilei on 2007-05-02
Thanks. I tried about ten different apps on XP but only GetDataBack and PC Inspector File Recovery (freeware) recovered anything. In all I recovered about half  my data. I've also bought a backup drive  : )

---

