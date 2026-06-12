---
title: "how do I set up a thumb drive to autosync a folder"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by mistergq on 2007-08-23
I want to have a folder automatically sync to a thumb drive.  I am using Kubuntu.  Is there a way to set up when that specific thumb drive is plugged into the computer it auto syncs?

---

### Post by p_quarles on 2007-08-23
I'm not aware of any GUI setting that would do this automatically, but I do have an idea. In Gnome (and I'm assuming this is possible for KDE) you can instruct it to auto-run programs upon inserting a storage device. So, if you were to put an rsync script on the thumb drive, make it executable, and turn-on the "auto-run" feature, you should be able to get the effect you're after. 

I'm inspired to try this myself, now, but won't be able to get to it tonight. If it works for me, I'll come back and share the script.

---

### Post by callan79 on 2007-08-23
> **mistergq said:**
> I want to have a folder automatically sync to a thumb drive.  I am using Kubuntu.  Is there a way to set up when that specific thumb drive is plugged into the computer it auto syncs?

I have a magazine article at home that I scanned to a PDF, and it guides you through writing a script that runs when you plug your USB stick in. The script takes a 'snapshot' of the USB stick, but it's should be a piece of cake to change that script to just copy files to a given directory on your hard drive.

If you PM me with your email address, I'll happily email you a copy of the article and you can give it a try .... looks long-winded and I have not yet tried it, but it has merit.

BTW - you also need to think about the definition of 'sync' - it's easy to copy files in one direction or the other direction, but detecting which one is newer will need some more thought as to the best way to do that, without risking overwriting your data!

Cheers
Callan

---

### Post by p_quarles on 2007-08-23
> BTW - you also need to think about the definition of 'sync' - it's easy to copy files in one direction or the other direction, but detecting which one is newer will need some more thought as to the best way to do that, without risking overwriting your data!
The rsync utility can automatically choose the newest file, actually.

---

### Post by HermanAB on 2007-08-24
Here is the right way to do it:
Figure out where the automounter script for the USB drive is and hook into the bottom of that.

Hint: It is somewhere in /etc
:)

---

### Post by mistergq on 2007-08-24
Callan - you rock!  

Your question about Sync is a good one.  In this particular instance, it will be one directional - from laptop to thumb drive.  I have one particular folder that if I were to ever lose, I will be up a creek.  I often copy it to other network drives and back it up to cds.  But a thumb drive would be much easier as an immediate solution.  I would still back it up to other media as well, but the thumb drive can be done much easier.

---

