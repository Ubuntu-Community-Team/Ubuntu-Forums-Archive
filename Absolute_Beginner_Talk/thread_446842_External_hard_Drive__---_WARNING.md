---
title: "External hard Drive  --- WARNING"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by micfreedom on 2007-05-17
[COLOR="Blue"]Backing up is extremely important, as it is so easy for "things" to go wrong.

A word of warning. *Choosing the right device*, memory stick, external hard drive, etc., is also extremely important.
Choice: There may be many devices that will help you back up your work. Make sure, though, that they are compatible BOTH for Windows and Ubuntu.
I lost my data, because I trusted them with My Book Essential external hard drive - made by Western Digital! At first, the hard drive worked fine. I trusted it to save all my data in it. 
Then, when I loaded Ubuntu, I could see the partitions, but the NTFS files could not be read or accessed. (I did not know that you could download the program ntfs-g3 for this specific purpose, and don't know whether this would have made my tast simpler).
Anyway, I put the external drive in my wife's computer USB plug, but Windows would not recognize it any more, even as I had downloaded Windows Service pack SP2 - as  Microsoft knowledge Base say that this might be the problem with recognition of hard drives! Nothing doing!.
I decided I would repartition my computer. I  still could not access the files on the hard drive.

I think somehow, I must have erased the data even thoughI saw the name I had given to the file, it was empty :(.
I wrote to Western Digital - which manufactures My Book Essential. They replied that if I could not have the hard drive recognized by another computer (my wife's) that I should replace it!
I have sent the device back to Western digital.
Sadly, it does not give my data back!
I have re-installed Windows and used Bystore 128 MB where I had an older version of my data. This works fine, so it is, fortunately a partial loss.
Let this be a warning, Not all back up devices work with both Windows and Ubuntu Linux. Test them with some inocuous files before hand, on Windows AND Ubuntu.
Sorry for this, but it's better to be safe than sorry.
Yours - keep th good work going.[/COLOR]

---

### Post by Quintin Riis on 2007-05-17
Since I don't use Windows, I'm kinda wondering why I need anything to be compatible with it.  

This is a case of user error or hardware failure.  That drive works fine with both Linux and Windows.

Use ext3 in the future if you want to share data between Windows and Linux.

Also might want to have a local expert look at the drive before putting it in the mail..

Sorry about your loss, that kind of stuff always stinks.

---

### Post by H.E. Pennypacker on 2007-06-18
What makes you so sure there was a hardware failure?  Why can't it be that the hard drive's partition table was corrupted, or something else not as dangerous as a hardware failure had occured?

You should have tried using My Book under Ubuntu to see if it could mount the hard drive.  You should have also used TestDisk to see if anything could have been done.  You gave up way too quickly.  

Another guy has reported he had no problem with Western Digital My Book, and uses it on Ubuntu.

---

