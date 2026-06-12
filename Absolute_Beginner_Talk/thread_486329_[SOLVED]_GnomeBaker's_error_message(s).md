---
title: "[SOLVED] GnomeBaker's error message(s)"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-06-27
I'm trying to copy Canonical's Ubuntu 7.04 as in .iso to my desktop, so that I can burn .iso duplicates to give to friends who want Ubuntu.

When I asked GnomeBaker to make a data CD, this is the response:

Read  speed:  7056 kB/s (CD  40x, DVD  5x).
Write speed:  7056 kB/s (CD  40x, DVD  5x).
Capacity: 357473 Blocks = 714946 kBytes = 698 MBytes = 732 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file '/home/mark/gnomebaker.iso'
end:    357473

0 00 80 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 4096.

m: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 16896.

eout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 25984.

US)

cmd finished after 0.000s timeout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 88960.
 Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 152704.

Status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 225152.

0 80 00

status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
readom: Cannot allocate memory. Cannot read source disk
readom: Retrying from sector 297600.

Is there a quick & dirty way to make ubuntu .iso copies?

I had to modify some of these lines, as they had  ...........  so many that the forum wouldn't let me post.

---

### Post by tcoffeep on 2007-06-27
Try ISOrecorder (I think thats what its called). It's freeware, and totally capable.

---

### Post by jimrz on 2007-06-27
> **tcoffeep said:**
> Try ISOrecorder (I think thats what its called). It's freeware, and totally capable.

Brasero, available through Synaptic does well for me

---

### Post by Mark_in_Hollywood on 2007-06-27
To:

tcoffeep

isorecorder is a windows program, as far as I can figure.

Anybody reading this post got an idea as to how to fix my problem with GnomeBaker?

It took time to download/install GnomeBaker. I think it works, I've copied 686 meg of pdf to a cd-r and it works. So, please, somebody tell me how to make it make an .iso.

---

### Post by Mark_in_Hollywood on 2007-07-15
Fixed -- well sort of --

right click on icon, "copy to", burns .iso automagically.

---

