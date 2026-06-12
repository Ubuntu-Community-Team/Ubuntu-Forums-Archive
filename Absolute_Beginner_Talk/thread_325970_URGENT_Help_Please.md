---
title: "URGENT Help Please"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by fca_neo on 2006-12-26
I deleted many important documents. Is there any way of having them back,

I was moving my home partition to its own partition following this guide ([http://www.ubuntuforums.org/showthread.php?t=46866)](http://www.ubuntuforums.org/showthread.php?t=46866)). Everything went fine, untille the en when I did this sudo rm -rf /homeOLD.

It errased very important files that where in a partition mounted in /homeOLD.

Is there any way of having them back?

Please help me,

Thanks

---

### Post by MkfIbK7a on 2006-12-26
im so sorry but you probably cant get them back :( 

however someone else might post a way that you can :D

---

### Post by fca_neo on 2006-12-26
I feel so stupid and bad.

I've just erased my entire music collection, two years of university work (notes and class slides), all my pictures, and many other things I may not remember. More than 20Gb of precious data is gone :(

---

### Post by MkfIbK7a on 2006-12-26
its all right we all completely delete something important some time mostly more than once:-\"

---

### Post by Sef on 2006-12-26
First, don't save anything to that computer.   Saving will overwrite files, so you may lose the important documents.

Second, here are a couple of rescue disks to check out:

[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")


[Trinity Rescue Disk]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12")

---

### Post by jmaryinchina on 2006-12-26
There is a way to recover the most important informations you had, the ones in text files.
But it's painfull and you have to umount the partition where you lost files were asap. Don't proceed anymore writing on this partition.

mondo is your friend : apt-cache search mondo -f

Install it and read the doc.

---

### Post by Sef on 2006-12-26
> im so sorry but you probably cant get them back

Not true.  You can recover lost information.   Sometimes you need to pay for it.   Sometimes the links I provided can do it.

> I feel so stupid and bad.

I've just erased my entire music collection, two years of university work (notes and class slides), all my pictures, and many other things I may not remember.

We have all done stupid things at times, so don't feel too bad about joining the club.

---

### Post by MkfIbK7a on 2006-12-26
actually the author of that post says you can restore your system from the comand line mybe you should ask how over there

---

### Post by scrooge_74 on 2006-12-26
I think you just join the club of "ups I just deleted important files"

You have no idea how many times in the last 10 years I have done that :D

---

### Post by MkfIbK7a on 2006-12-26
yes i know sef i just forgot to read the post he had in that link but i read it and i think mybe his files can be recovered now:D:D

---

### Post by maddog39 on 2006-12-26
> **fca_neo said:**
> I deleted many important documents. Is there any way of having them back,

I was moving my home partition to its own partition following this guide ([http://www.ubuntuforums.org/showthread.php?t=46866)]("http://www.ubuntuforums.org/showthread.php?t=46866%29"). Everything went fine, untille the en when I did this sudo rm -rf /homeOLD.

It errased very important files that where in a partition mounted in /homeOLD.

Is there any way of having them back?

Please help me,

Thanks
Hey! Dont feel bad, I deleted the hard drive on my dedicated server and it cost $120 to fix. :P

Beware of rm -rfv / :O

---

### Post by smoker on 2006-12-26
hi, if you can, download ubcd from here:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

burn the iso to cd and boot from it, there are some recovery apps included, one of which is 'active@partition recovery'

sorry, ignore the active@partition recovery app, just found it is only for windows/dos!

---

### Post by fca_neo on 2006-12-26
I'm glad to see there is a bit of hope. I'll try the recovery tools you suggested Sef.

I unmounted the partition as soon as jmaryinchina said it.

I installed testdisk and I'm trying it right now.

I'm also downloading Trinity RD and i'll burn it as soon as i get it.

Thanks guys for the quick reply

Btw, What do you things is the chance of recovering data such as pdfs and pictures?

---

### Post by fca_neo on 2006-12-27
I have read a lot onest3 file system and i have not found any convenient ways of recovering the files. The only sort of way i found is to grep (or something like that) all the partition content into a text file and try to eyeball the files from the text or binary strings, which is painful (I have been using linux for less than two weeks now, so i don't know much stuff about it)

Also, I don't really know how to use the tools you proposed, sorry.

I tried several automatic tools but I had no success. 

I'm mainly interested in recovering .pdf. .doc, and .jpg files. 

Do you think I have any chance of recovering them? I have not written to the partition since the delete, are the files still intact?

If there is a chance of recover, then I would save the partition content for a file and try to extract it by hand, else I'll go on with my life and I will rebuild my documents.

---

