---
title: "Backup solution"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-06-20
Anyone know of a good dvd backup solution?

My current problems using DVD include:

-Problems with long filenames
-Drirectories being too deep
-lots of data, at least 5 disks worth.
-trying to plan how to fit them onto the disks

I could use RAR to make 4.3gig chunks i guess but this is really slow and have to burn each one manually. 

I was hoping there was a better solution where i could choose the dirs i want to backup and then just click GO.
The program would then create a compressed spanned backup on DVDs where the only input needed from me is "please insert next disk"

---

### Post by Inxsible on 2007-06-20
Getting additional hard drives is one of the solutions, if you are not averse to it.
 
They are pretty cheap these days, with [500 GB costing around $120]("http://deals2buy.pgpartner.com/search_getprod.php?masterid=17987372")
 
and 1TB costing approx $330
[1TB for $333]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1129520")

---

### Post by orb9220 on 2007-06-20
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)
For backup of partitions.

Or look into simple backup in synaptic.

Command line backup commands are:
Tar and rsync

search synaptic on **backup** will list others

---

### Post by ramjet_1953 on 2007-06-20
I just bought another HDD and put it into one of those little USB enclosures. However if you have a desktop, you can get similar external enclosures, as well.

I then downloaed Ghost for Linux (G4L) and burnt the iso to a CD.

To do a clone of my HDD, I just plug my external HDD into a USB port, boot from the Ghost for Linux CD and choose the local cloning option.

Works like a charm and produces an identical copy of my HDD.

Note: when copying a HDD it can take quite a while, using USB. My 120 GB HDD takes about 3.5 hours to clone.

Regards,
Roger :cool:

---

### Post by dgrafix on 2007-06-21
I tried the simple backup but its no good. It doesnt seem to have any spanning to disk option, and doesnt seem to give any progress indication of how the backup is going or anything.
As for ghost, thanks for pointing that out!! that will definitely be useful for making a system image :) but is unfortunately a bit overkill for a weekly backup of a few dirs.

I already have an external harddisk which i use with RSYNC to mirror my main disk, but need a disk solution for an off site backup in case of theft, fire etc. I would buy a tape drive but they all seem to be scsi and have ridiculous price tags :/

It would be nice if there was a tool to create a TAR file in 4.3 GB chunks that can be written to disk then burned manually. 
Prehaps TAR does this but the --help is always sooo cryptic on command line tools i dont know what its all talking about half the time.

From my attempts at deciphering the help im guessing something like:

tar -cfML, --tape-length=4300x1024 /media/disk-1/mybackup.tar /home/.
and
tar -cfML, --tape-length=4403200 /media/disk-1/mybackup.tar /home/.

but it didnt like those at all. 

The parameter standard for linux seems confusing, ie when the help says: "-L, --tape-length=NUMBER"    does this mean you litterally type it like that or simply use "--tape-length=" if so, what is he -L for?

---

### Post by orb9220 on 2007-06-21
[http://ubuntuforums.org/showthread.php?t=35087&highlight=HOWTO%3A+tar](http://ubuntuforums.org/showthread.php?t=35087&highlight=HOWTO%3A+tar)

---

### Post by Taliskerd on 2007-06-21
Not quite what he's after, I think..

For my 2 cents, I'd point you to the abs-guide (hidden in the Synaptic manager) for what seem to be a pretty thorough bash scripting guide.

Also note that 'man tar | grep L'  show 
...
Function Letters 
  -L, --tape-length N
...

Which mean that L and tape-length are BOTH valid arguments for telling tar how large you want the archive parts to be.

I guess you'll end up scripting something that tar your files and then call a dvd writer to end your misery.
On the other hand, you'll only need to do the hard work once ;)

---

