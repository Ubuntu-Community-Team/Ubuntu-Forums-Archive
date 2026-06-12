---
title: "I/O error: cannot get past start up screen:"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by MarcTH on 2006-09-11
I have lurked and scanned around here for a very short while and I suspect I am about to put myself up for the dumbest newbie award!

Ubuntu 6.06.1 has been downloaded, a live CD has been created, the CD drive has been moved to number one priority for start up, the Ubuntu start up screen appears when I reboot but then on any selection I make I receive the error message:

I/O error

Error reading boot CD

Reboot


I have tried making a 2nd CD but with the same result, I know that the CD/DVD drive works ok (when using 'that other' OS) so I would be really grateful if anyone could guide me through some troubleshooting.

I am determined to be persistent so I expect to be back here on a regular basis but I really didn't expect a hurdle this basic this early!


Thanks in advance,

Marc.

---

### Post by mssever on 2006-09-12
It appears that you have either a corrupted ISO or a couple of bad burns. Do you get the initial boot splash? If not, make sure that you burned the ISO properly. Simply copying the ISO to the disc will NOT work. You might find [this guide]("http://psychocats.net/ubuntu/iso") to be helpful.

---

### Post by MarcTH on 2006-09-13
Thanks mssever.

I will go and take a look at your link.  When I boot from the LiveCD I do get into what I would call a start up screen which offers various options including installation and is definitely the Ubuntu starting point - is this what you mean by the initial boot splash?

Marc.

---

### Post by mssever on 2006-09-13
Yes, you got to what I called the boot splash. If I remember correctly, there is an option to test the CD. You should try that. My gues is that it will fail. In that case, you need to check the md5sum of the ISO you downloaded. The link I gave tells how to do that. If the md5sum fails, you need to re-download. If it succeeds, try burning at a lower speed.

---

### Post by Repus on 2006-09-13
Try the cd in other machines if it works try the solution below. I have found that some writable cds can not be read fully by some cdroms. 

All I needed to do to fix this problem on my system was burn to a different brand of cd _or_ swap out the cdrom drive with a different manufacturer and it works. Go figure.

---

### Post by MarcTH on 2006-09-14
> **mssever said:**
> Yes, you got to what I called the boot splash. If I remember correctly, there is an option to test the CD. You should try that. My gues is that it will fail. In that case, you need to check the md5sum of the ISO you downloaded. The link I gave tells how to do that. If the md5sum fails, you need to re-download. If it succeeds, try burning at a lower speed.


Thanks again mssever . . . 'Checksum did not match', so I'm off to learn about BitTorrent now!

Will check in later!


Marc.

---

### Post by MarcTH on 2006-09-14
Thanks Repus, I've gone out and got myself some better quality CDs from a different brand in preparation for a successful and verifiable download!

Marc.

---

### Post by MarcTH on 2006-09-14
I'm missing something with this BitTorrent lark(!) . . . . estimated download time of 346 hours (BitTornado/Firefox) vs 6 hours normal download on my ADSL (this is Thailand!).

Got a busy couple of days coming so may not be able to concentrate on getting this done until Monday but I am going to go and try to understand BitTorrent - any hints or advice gratefully received.  In the meantime I'm going to try a normal download and see if I can successfully verify the file this time.


Thanks

Marc.

---

### Post by MarcTH on 2006-09-28
Okay . . . that took longer than expected!  We're in the middle of a military coup here but that's no excuse as it is the most civilised coup ever and all is pretty much business as usual.  However my baby daughter has been really sick (fine now) so my attention was on her.

Anyhow - couldn't get BitTorrent to help but managed to verify a regular download with md5sum and managed to burn the ISO onto a different brand of CD at a much slower speed (8x).  In Windows the CD came up with the appropriate Ubuntu screen and then I booted from the CD and received the following:

Starting . . .

Loading Linux Kernel

- - - - - - - - - - 100%

At which point I was starting to grin and then . . . :

I/O error

Error reading boot CD

Reboot


Aaargh!

I really don't fancy the idea of swapping out my CD drive so are there any other troubleshooting routes or suggestions on how I can get over this first hurdle?


Many thanks in advance,

Marc.

---

### Post by mssever on 2006-09-28
I'm assuming that you've tested the CD using the CD's test option? I'm really not sure what's going on. If I were you, I would try to boot another computer from your CD (if you're using the live CD, you can do that without affecting the other computer in any way). If it boots, then you know that something' weird with your hardware. If it doesn't, then something's probably weird with the CD--or your CD burner.

And you might end up swapping CD drives.

---

### Post by MarcTH on 2006-09-30
> **mssever said:**
> I'm assuming that you've tested the CD using the CD's test option? I'm really not sure what's going on. If I were you, I would try to boot another computer from your CD (if you're using the live CD, you can do that without affecting the other computer in any way). If it boots, then you know that something' weird with your hardware. If it doesn't, then something's probably weird with the CD--or your CD burner.

And you might end up swapping CD drives.




I did try the CD test option which produced the same result but . . . . . 

Hallelujah and praise be to the Canonical guys, 5 Cds arrived in the post today and, guess what???  Their CDs work!!   I'm the happiest puppy this side of Delhi!

Now I need a dummies guide to keeping all my .doc .xls .ppt .pst .jpg .gif etc etc files and moving over with no loss od data and minimal cerebrial discomfort!

Any hints?


Marc.

---

### Post by mssever on 2006-10-03
There's a lot of good info at [http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/). Basically, when you get to the section of the installer that asks you to set up partitions, *don't* let it erase your disk. There's an option to resize your current partition and dual boot (if you don't want to dual boot, simply copy the files you want to keep to remoable media of some sort).

If you dual boot and want to be able to write to your NTFS (Windows) partition, install ntfs-3g from the instructions here: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by jtanium on 2006-11-01
If it helps anybody, I was finally able to get past this by burning the isos on my Mac using [FireStarter FX]("http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter").  I tried burning the images using Nautilus on Fedora (5 & 6)and Dapper, and Disk Utility on OS X.  I'm kinda disappointed at how much of a hassle this has been...

---

### Post by kasfour on 2007-02-03
I encountered this exact, same problem with Ubuntu 6.10.  As strange as it sounds, it turned out to be a bad download of the ISO...

My first download was about 700 MB, from which I burned the CD.  I was able to reach the initial Ubuntu menu (where you can choose "Install," "Inspect CD," "Safe Mode," etc.), but any selection resulted in an "error reading boot CD."  When I went back to inspect the ISO (which I had downloaded to my Mac), I noticed that the file reported a size of only 217 MB---even though I was SURE that I had pulled down close to 700 MB when downloading the file (I was periodically monitoring the status bar).  What's **really** weird is that I could successfully mount the ISO file as a volume on my Mac, and when I did, the volume weighed in at 698 MB.

So I downloaded the ISO again; this time the file reported a size of 698 MB.  I burned it, and installed Ubuntu without any problems.  The lesson, I suppose, is always check the MD5.

---

