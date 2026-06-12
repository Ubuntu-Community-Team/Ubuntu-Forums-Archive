---
title: "Mount old Mac CD-ROM on Ubuntu 8.04"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by aer0usa on 2009-01-22
Hi,

I have a CD-ROM I burned from my old Mac, back in the System 7 days. I'm trying to mount the CD on my new Ubuntu machine to get at some of my old docs. 

When I try to mount the CD, I get an alert box with the following message: 
Cannot mount volume. Invalid mount option when attempting to mount the volume 'Banana Jr.'.

So, I'm kinda new at this Ubuntu thing. I'm not sure what file system the CD is. HFS? HFS+? I don't think I made this one ISO9660.

I looked at the mount man page, but I didn't seem to be getting anywhere. I tried 'mount -t hfs /dev/cdrom /home/mydir/bjr' and 'mount -t iso9660 /dev/cdrom /home/mydir/bjr' and was told that the file system may be incorrect.

Can someone give me a pointer? Thanks!

Edit: Here's exactly what I get:
aer0usa@Ubuntu:~$ sudo mount -t hfs /dev/cdrom /home/aer0usa/bjr
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by avtolle on 2009-01-22
One problem imo is the name of the volume "Banana Jr." due to the space in the name.

EDIT: Sorry to cut off that post. One option would be, IIRC, to enclose the entire name of the volume in quotation marks and try it again.

---

### Post by avtolle on 2009-01-22
Rereading your edit, it seems that hfs is not the correct file system, and I'd wager it is hfs+, as your attempt to mount as an iso also failed. I've a feeling you may need to get to a mac with a mac OS installed to get to the files, although others with more experience may have a better idea.

---

### Post by aer0usa on 2009-01-22
Thanks avtolle. That's just the one attempt that I copied to show. I tried -t iso9660 and got the same results. I also tried -t hfs+ and it said 'unknown filesystem type'.

From your first reply, since I'm referring to the CD as '/dev/cdrom' and not entering its volume name anywhere, I'm not sure where I'd put the volume name with quotes around it. I can see where the odd volume name might cause a problem though. When I named that volume eleven years ago, I really wasn't thinking that I might someday try to mount it on a Linux machine! :)

---

### Post by avtolle on 2009-01-22
On hfs+, it seems to me I recall that this file system is not recognized by Linux unless the journaling is turned off. No expert at all; never used the Mac OS on the 2 Cubes of which I am the beneficiary, just installed Ubuntu on them when I received them (given the age of the OS, etc.). I'll think about your other issue, too.

---

### Post by avtolle on 2009-01-22
Took a quick look at man mount. try "hfsplus" instead of "hfs+" (without quotes, of course) in your mount command. If you already did this, disregard.

---

### Post by cyberdork33 on 2009-01-22
> **avtolle said:**
> Took a quick look at man mount. try "hfsplus" instead of "hfs+" (without quotes, of course) in your mount command. If you already did this, disregard.+1

Also, journaling wouldn't be enabled for a read-only CD :)

---

### Post by avtolle on 2009-01-22
> **cyberdork33 said:**
> +1

Also, journaling wouldn't be enabled for a read-only CD :)

Yes, that's true (why do I type before thinking?). Thanks, cyberdork33.

---

### Post by aer0usa on 2009-01-22
Same result:
```
aer0usa@Ubuntu:~$ sudo mount -t hfsplus /dev/cdrom /home/aer0usa/bjr
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Am I using the 'mount' command properly? 

I looked in the syslog like it suggests, and I don't see anything that's not in the message.

What's 'dmesg | tail or so'?

What about the mount point I've selected? '/home/aer0usa/bjr' is an empty folder I've created. Is that how that's supposed to work?

Thanks for looking into this, both of you!

---

### Post by cyberdork33 on 2009-01-22
> **aer0usa said:**
> What's 'dmesg | tail or so'?
Type:
```
dmesg|tail
```
after you try to mount.

You might try not specifying the filesystem type and see what happens.

```
sudo mount /dev/cdrom /home/aer0usa/bjr
```

---

### Post by aer0usa on 2009-01-22
The results:```
aer0usa@Ubuntu:~$ sudo mount /dev/cdrom /home/aer0usa/bjr
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type
aer0usa@Ubuntu:~$ dmesg|tail
[11467.267156] end_request: I/O error, dev sr0, sector 1129168
[11467.269566] end_request: I/O error, dev sr0, sector 1129168
[11467.271833] end_request: I/O error, dev sr0, sector 1129168
[11467.273985] end_request: I/O error, dev sr0, sector 1129168
[11467.276147] end_request: I/O error, dev sr0, sector 1129168
[11467.278322] end_request: I/O error, dev sr0, sector 1129168
[11467.280601] end_request: I/O error, dev sr0, sector 1129168
[11467.356746] end_request: I/O error, dev sr0, sector 1129164
[11467.358911] end_request: I/O error, dev sr0, sector 1129168
[11467.361088] end_request: I/O error, dev sr0, sector 1129168
```

---

### Post by aer0usa on 2009-01-22
Apparently, this is a Linux bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/144481]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/144481")

In the past, I've copied files off of this CD onto Windoze using HFVExplorer. I'll go that route for now.

Thanks again to both **avtolle** and **cyberdork33** (possibly the best online handle I've seen!)

---

