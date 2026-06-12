---
title: "CDRW: Do not have permission to write to this file"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by nerves on 2007-01-10
Hi

I am just starting with Linux, have loaded in the latest version of Ubuntu.

I have connected an IOMEGA USB CD REWRITER, it has been excepted ok.

If using just a CDR it all works fine, but when I try to use a CDRW, I get 

ERROR WHILE COPYING TO "/media/cdrecorder" You do not have permissions to write to this folder.

I am using NAUTILUS 2.16.1 which came with the Ubuntu. 

The CDRW is an old one, formatted on Windows XP, but it is coming up as CDRW and shows that it is empty.

Any help/ideas would be great.

Thank you

---

### Post by viciouslime on 2007-01-10
Trying going to the places menu, then CD/DVD creator and dragging your files there. When you're done, click write to disc.

---

### Post by nerves on 2007-01-10
Thank you, 

Have just tried that, and am still getting the same error report.

---

### Post by louieb on 2007-01-10
Try this
Applications>Accessories>terminal
```
sudo chmod 777 /media/cdrecorder 
```This gives everybody permission to read and write to the directory.

---

### Post by nerves on 2007-01-10
Thank you

It has let me write to CDRW. 

It is saying the disk is full now, even though I only put a small file on to CDRW. Is this normal?

---

### Post by disophisis on 2007-02-21
Hey I was having the same 'you do not have permissions to write to that folder' problem with 25 gig partition on my hard drive -- this solution works perfectly, thanks a million.

I'm new to linux as well, but it's very exciting getting something to work. :)

---

### Post by rasbach on 2007-02-21
@ nerves

When you get this error message in Linux, and you know you have more than enough disk space- it normally means it cannot read how the disk is formatted.  This is true with both hard drives and other storage media.

Try to format the CD and then try it again.  It should fix your problem.

---

### Post by Wynne G Oldman on 2007-06-08
> **rasbach said:**
> @ nerves

When you get this error message in Linux, and you know you have more than enough disk space- it normally means it cannot read how the disk is formatted.  This is true with both hard drives and other storage media.

Try to format the CD and then try it again.  It should fix your problem.

How do I format a CD or DVD?

---

### Post by diddler on 2007-06-10
Most of the CD/DVD apps like GnomeBaker have a format function.  Tell it to format your CD/DVD RW.  I am about to see if it worked for me.

---

### Post by diddler on 2007-06-10
> **louieb said:**
> Try this
Applications>Accessories>terminal
```
sudo chmod 777 /media/cdrecorder 
```This gives everybody permission to read and write to the directory.

I tried this and first it said the device 'cdrecorder' did not exist, so I changed it to cdrom0 and got this message: [COLOR="DarkRed"]changing permissions of `/media/cdrom0': Read-only file system[/COLOR]

It still will not let me right to a DVD-RW formatted with GnomeBaker.  This is a Plextor PX740A.

---

### Post by Wynne G Oldman on 2007-06-11
> **diddler said:**
> Most of the CD/DVD apps like GnomeBaker have a format function.  Tell it to format your CD/DVD RW.  I am about to see if it worked for me.Hi, I tried that with K3B and got the following error message.

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
LITE-ON DVDRW SHM-165P6S MS0R (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Sequential mode detected.
umount: /media/DVD_VOLUME is not in the fstab (and you are not root)
:-( unable to proceed with format: Device or resource busy

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -blank=full /dev/scd0 

This is driving me round the bend. It must be something simple. Surely you can write to your DVDRW through Ubuntu?

---

