---
title: "Unable to MD5 checksum"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by villagereaver on 2007-08-07
I first started with [this thread]("http://ubuntuforums.org/showthread.php?t=232059") by ubuntu_demon written for me--the beginner.  I like the look (and feel) of Kubuntu 7.04 and d/l'd it from the site u_d listed.  I d/l'd the winMD5sum and infra recorder (following the instructions) and come up with a different MD5sum every time in five attempts.

I have a homebuilt system with dual 2.1Ghz processor(S?), 4Gb RAM, 300Gb ATA HDD and XP.  I have also tried at work on a Dell D610 laptop with Pentium M 1.73Gb, 512Mb RAM, 40Gb HDD and XP.

Five attempts all ending in failure.  Obviously I am missing a vital step or misinterpeting instructions.  I really want to end my reliance on Gateszilla and M$ (except for gaming of course ;) ).  I fantasize about teling l my computer what to do, not the other way 'round.

I have ordered the disks via mail, but would like to get going sooner rather than later.

Kubuntu site i downloaded from: [http://kubuntu.org/download.php]("http://kubuntu.org/download.php")
This version of Feistey Fawn has a checksum [here]("https://help.ubuntu.com/community/UbuntuHashes"), correct?  I am looking at the desktop i86 (non-alternate) showing [U]1ad3c003dbcbe27b3265da23b886d047
[/U].

The instructions [here]("https://help.ubuntu.com/community/HowToMD5SUM") seem (to me, at least) to indicate i checksum after download, but before i burn the .iso.  Is this true?  I (sorry to use Window-speak) searched the folder I downloaded & unzipped to and found only two .iso files to checksum.

Thank you, demiurgicdaemon, for the additional MD5 sum utility, but i still come up different.

---

### Post by demiurgicdaemon on 2007-08-07
If the MD5 sum is different before you burn to cd then first try another program like this one.  [http://fileforum.betanews.com/detail/MD5_Fingerprint/1119188460/1]("http://fileforum.betanews.com/detail/MD5_Fingerprint/1119188460/1")
If you are calculating the md5 sum after you burn to verify the burn and it is not working, then burn at a low speed like 4X.  I have had many problems in the past with burning ISOs correctly.  Burning at a low speed always fixes this problem for me.

---

### Post by villagereaver on 2007-08-08
Now i am to the point of asking, "How important is it that I perform this test?"  

Can I, with low likelihood of devastating effect (affect?) on install skip this step?  Should I not take the chance?

---

### Post by ron999 on 2007-08-08
Hi
The reason for performing the test is to check whether the file has got corrupted when downloading.
You can go ahead without doing the test, but if it does turn out to be corrupted then you probably won't get the LiveCD to run.
You will have wasted a CD-R.
(Though you could use a CD-RW instead)

---

### Post by villagereaver on 2007-08-10
Hopefully this will help someone else from making my mistakes.  

I was confused by the fact that WinRAR showed the _whole_ d/l'd file as .rar, not .iso (which, apparently is what it is as well).  Once I understood that i needed to check the entirety of the d/l, rather than searching for .iso files inside it, I got good checksums.

---

