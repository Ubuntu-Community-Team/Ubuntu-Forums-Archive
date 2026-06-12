---
title: "dev/sda1/ has been mounted 35 times"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by mamasita on 2008-03-21
hello I have read threads on this but I am having a problem with my hp laptop.  It never finishes booting.  It hangs around 30.3%.  Is there a way to by pass that just for today so I could get some really important files.  I really do not want to spend all weekend working on a research paper.  Oh maybe this might help I was at a holiday in express and I was directly plugged in to my laptop for internet access would this cause my computer to hang up?  Pleas help thanks.:confused:

---

### Post by herbster on 2008-03-22
This is the fsck command automatically checking your drive. How long have you waited while it scans and how many times have you rebooted and encountered the same thing?

---

### Post by Hospadar on 2008-03-22
You could boot off a livecd and use gparted to check the drive and get at your files.  To run gparted from the livecd, Alt-F2 and type "sudo gparted" right click the partition ubuntu is installed on and check it, and apply the actions.

Also in the livecd if you go to Places->Computer you can easily mount your drives and get at your stuff until you get things straightened out.

After you get things fixed up, you can use the program "tune2fs" to change how the automatic checking behaves, a "man tune2fs" or a google search should give you some good clues as to the command line options

---

### Post by famous3warriors on 2008-03-22
Hey I have the same problem I will do what they suggested.  Thanks once again.  Good luck mamasita.

---

