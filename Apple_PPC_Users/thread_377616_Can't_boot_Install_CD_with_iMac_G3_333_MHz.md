---
title: "Can't boot Install CD with iMac G3 333 MHz"
date: 2007-03-06
forum: Apple PPC Users
---

### Post by langerak on 2007-03-06
Hi there,

I've been wanting to try Linux on my old iMac G3 for some time now and i've given it a try today.

Downloaded the latest release for the PPC platform, burned it and placed it in my CD-ROM drive of the iMac.

When it boots, a error message keeps scrolling forever saying this:

DEFAULT CATCH!, code=300 at  %SRR0: <random memory address>  %SRR1: 0000b030

Googled for it, no explanation tho, so here is my question: How can this be fixed?

It's a iMac G3 333 MHz Orange, Tray loading, 192 Mb RAM and 40 Gb MAXTOR Disk.

Any help would be appreciated!

---

### Post by rondackcpu on 2007-03-16
I have an old 'Blueberry" with even less memory which was entirely useless with OS 9.1 and OS 10.0.  I have been successful in installing both Ubuntu or Xubuntu on it (one at a time) with very pleasant results.  Several times I got the same response from the boot attempt that you report.  I don't know what the problem is, but I suggest you keep trying.  Take the disk out of the tray, blow off the imaginary dust particles, put it back in, and try again.  

I seem to have settled on Xubuntu for now as it seems a bit faster with my 160 meg memory.

Good luck.  You'll enjoy the revival of your iMac.

---

### Post by rccharles on 2007-03-16
> **langerak said:**
> Hi there,

I've been wanting to try Linux on my old iMac G3 for some time now and i've given it a try today.

Downloaded the latest release for the PPC platform, burned it and placed it in my CD-ROM drive of the iMac.

I'm have successfully installed Ubuntu 6.10 on my iMac g3 600 using the Ubuntu 6.10 alt cd.

 I had to comment one line in my xorg.conf file. See the above link. I haven't gotten the modem to work yet. I believe people have gotten the modem to work on the 333. See:
[http://www.ubuntuforums.org/forumdisplay.php?f=133](http://www.ubuntuforums.org/forumdisplay.php?f=133)

Ubuntu has a minimum memory size. I think it is 128meg.

Robert

---

### Post by trackin_fool on 2007-04-06
Did you boot that Blueberry from within the Mac OS?  I have a Blueberry that has an Mac OS but I can't get it to boot into it.  I don't have a Mac CD either.

---

### Post by vadriaan on 2007-04-07
I tried booting a couple of different versions of PPC  Linux. The laptop does not seem to recognize these CDs as bootable CDs. I even ordered a "commercial" version of Ubuntu in case my x86 is doing a bad job of writing a PPC boot CD. The laptop boots from the Mac OS 9.3 CD but not Linux. I was wondering if one needs to burn a PPC boot CD exclusively from a PPC machine and not use a x86 at all?

---

### Post by rondackcpu on 2007-04-07
I have a very old Blueberry which I have (since the above reply) upgraded with 512 MB memory.  I have had very good results installing any of these:  6.04 Alternate CD, 6.10 Alternate CD, and 7.04 Alpha Herd 5 Alternate CD.  The secret seems to be burning the CD at very slow rates.  I have had good results with CDs burned at 4X.  Somewhere I read that the iMac's hated CD-R's, so try the slow burn.  The Live Cds seem not to work out for me as they turn off the CRT power supply at the critical moment of starting "X".  No way to see what is going on after that.

The 7.04 Beta ISO is 730 MBytes, and my CD burner (a Wintel machine with Ubuntu 7.04 Beta installed) refuses to burn the 7.04 Beta ISO.  Has anyone discovered a work around for this problem?

CRS

---

