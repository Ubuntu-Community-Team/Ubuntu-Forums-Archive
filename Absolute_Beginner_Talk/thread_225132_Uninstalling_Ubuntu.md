---
title: "Uninstalling Ubuntu"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by OzFred on 2006-07-29
I can't believe uninstalling Ubuntu isn't an FAQ, anyhow...  

A search of the forum here didn't turn up a lot of help, I've managed to fix the master boot record and delete Ubuntu so now I can boot back into Windows just like before.

I managed to turn the two partitions that the Ubuntu install created into one partition, now I'd like to put it all back as part of my C: partition.  I only have a small HDD (6GB) and having two partitions wastes quite a bit.

For those who are trying to remove Ubuntu, here's what I did:

Boot from a Windows CD (I used Windows 2000).

Go into the 'restore Windows' bit and use the restore console (press C, not R).  If you think your drive has issues, use R and restore first, then re-boot from the CD again.

You will need an administrator password to get to the console command line.  Once there, run fixmbr and then fixboot (type in fixmbr and press enter, same for fixboot).

They return your master boot record back to automatically run Windows.  You'll get some dire warnings...  Remove the CD and reboot.

Once you get Windows running again, login as an administrator, go into the management utilities and delete the two partitions that Ubuntu created (they don't have drive letters).  They will form  back into a single, unallocated portion.

You can now partition and format them, but they will be a separate logical drive from the original C: drive. 

So that's where I'm up to - anyone care to suggest how to go back to a single C parition (yeah I know I could re-install Windows)?

Cheers, Fred.

PS.  I think Ubuntu is pretty good, and will likely turn my Laptop into a pure Ubuntu PC, but not just yet...[http://ubuntuforums.org/images/smilies/icon_cool.gif](http://ubuntuforums.org/images/smilies/icon_cool.gif)

---

### Post by codejunkie on 2006-07-29
> **OzFred said:**
> I can't believe uninstalling Ubuntu isn't an FAQ, anyhow...  

A search of the forum here didn't turn up a lot of help, I've managed to fix the master boot record and delete Ubuntu so now I can boot back into Windows just like before.

I managed to turn the two partitions that the Ubuntu install created into one partition, now I'd like to put it all back as part of my C: partition.  I only have a small HDD (6GB) and having two partitions wastes quite a bit.

For those who are trying to remove Ubuntu, here's what I did:

Boot from a Windows CD (I used Windows 2000).

Go into the 'restore Windows' bit and use the restore console (press C, not R).  If you think your drive has issues, use R and restore first, then re-boot from the CD again.

You will need an administrator password to get to the console command line.  Once there, run fixmbr and then fixboot (type in fixmbr and press enter, same for fixboot).

They return your master boot record back to automatically run Windows.  You'll get some dire warnings...  Remove the CD and reboot.

Once you get Windows running again, login as an administrator, go into the management utilities and delete the two partitions that Ubuntu created (they don't have drive letters).  They will form  back into a single, unallocated portion.

You can now partition and format them, but they will be a separate logical drive from the original C: drive. 

So that's where I'm up to - anyone care to suggest how to go back to a single C parition (yeah I know I could re-install Windows)?

Cheers, Fred.

PS.  I think Ubuntu is pretty good, and will likely turn my Laptop into a pure Ubuntu PC, but not just yet...[http://ubuntuforums.org/images/smilies/icon_cool.gif](http://ubuntuforums.org/images/smilies/icon_cool.gif)

you should be able to use the ubuntu desktop/live cd and use gparted to recover the diskspace.

---

### Post by Apple 101 on 2006-07-29
Do you have Partition Magic or another disk management tool?  If not, you may like to look at the GParted Live CD.

Another option is to move your documents, music, etc. to the second partition, to use the partition for document storage.  Moving 'My Documents' is simple.

---

### Post by OzFred on 2006-07-29
Thanks codejunkie,

I used the Ubuntu CD to make one partition, but then Windows wouldn't boot because it couldn't find the boot sector... so... back to booting from the install CD, ran fixboot, then chkdsk /p just in case, but no luck.

I couldn't continue with two partitions because I only had 500MB spare on the boot partition.

I'm now back to re-installing Windows from scratch.

---

### Post by Apple 101 on 2006-07-29
You need to run *fixmbr* from the Windows Recovery centre, or using a boot floppy, *fdisk /mbr*.

---

