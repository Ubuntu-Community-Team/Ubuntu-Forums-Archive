---
title: "Sata slows down startup"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by patrickbway on 2008-01-13
Hi 

I use ubuntu on an ide hard drive and its boots up nice and quick. However, when I have my sata plugged in, which has winxp on it, it takes ages to boot, and sometimes just hangs on the Ubuntu progress bar.

I went to the recovery to check out what it was loading, and it looked like it kept retrying to load up the sata and it was is not managing.

Any ideas on how to speed this up?

I could just plug in my sata when ever i want to boot xp, but its a bit of a hassle always pluging things in and out! :D

---

### Post by njparton on 2008-01-14
Google sdparm.  hdparm (for ide drives) is installed by default, but sdparm is in the repositories and is very similar and is designed for SATA (and SCSI?) drives.

You'll need to install it and tweak your drives although I personally have never done it or needed to.

Also, check you have your bios set up correctly for the SATA channel you're using.  Options available will vary from motherboard to motherboard.

---

