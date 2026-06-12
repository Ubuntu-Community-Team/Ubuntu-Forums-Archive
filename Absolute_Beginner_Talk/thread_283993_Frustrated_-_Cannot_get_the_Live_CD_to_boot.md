---
title: "Frustrated - Cannot get the Live CD to boot"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by jalopyhead on 2006-10-25
I am really frustrated at this point. I've downloaded the cd image from the ubuntu.com website. As far as I know, I've done all that I'm supposed to do. In fact I've downloaded and burned at least 6 different cd's.

I cannot get the live cd to boot at startup. The computer says it is reading from cd, but then goes straight to windows. My computer is an Acer 3200 AMD sempron processor. (I've tried both 32-bit and 64-bit).

The most confusing thing is that I also tried it on my other computer - Dell inspiron 1100 laptop, but it doesn't do anything here either. This makes me think that it is my error, not the computer's. 

Can anybody offer help.

---

### Post by deepwave on 2006-10-25
Try checking the MD5 sum of the ISO image.  The mirrors include a .md5 file for every CD image.  If the md5 sum is off then the CD image is corrupted.

MD5Sumer is a nice Windows program for md5 sums.

Not sure how else to help... try noting any error messages you get if the system tries to boot from CD.

---

### Post by Dr. Nick on 2006-10-25
You sure its burned as a disk image and not a data cd? let it boot into windows and then go to "my computer" and open the cd drive, make sure it has several files and folders, not just a single file with .iso on the end

---

### Post by nickburns on 2006-10-25
I once had a similar problem because I was actually buring the iso file to the cd rather than burning the image to the cd.  There is a difference.  If you boot up some computer and put the cd in the drive, do you get the one iso file showing up on the cd, or is there several files/folders burned to the cd?

If all you see is one iso file burned to the disc, then you need to use some burning software to actually burn the cd 'image' to the cd.

---

### Post by Dr. Nick on 2006-10-25
If you only get the 1 file look here
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by jalopyhead on 2006-10-25
Thanks everyone for the super-quick replies.

I think I might know the problem. My computer associated the .iso with my unzip program (winrar) and I assumed it was a .zip file that I needed to unpack. Unfortunatly, I have already deleted the previous "unpacked" downloads - I am downloading it again right now. If I have anymore trouble I am confidant I can post again and people will respond - Thanks!

Dr. Nick - your tutorial link was especially helpful.

Jalopyhead

---

### Post by Dr. Nick on 2006-10-25
Ohh, yeah, if you just unzip it you will get all the files, but it wont boot. The problem is that the iso has a "boot sector" in it which gets written to the cd only when you "burn as image". If you just burn a unextracted iso that doesnt get written.

You dont need to umpack it or anything, as in the link you can just open and burning application and select "burn image" and point it to the .iso file

---

### Post by nickburns on 2006-10-25
Just a thought, if you have cd burning software (Roxio, Nero ...) then you probably can right click the iso file and do burn to cd.

---

