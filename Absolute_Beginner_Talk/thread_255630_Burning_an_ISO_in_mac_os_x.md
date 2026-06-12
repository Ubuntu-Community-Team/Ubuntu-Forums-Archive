---
title: "Burning an ISO in mac os x"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-09-11
I have ordered the ShipIt CD a while aago but I cant wait anylonger! I need ubuntu now! So I figured id go ahead and download it and burn it to a disk. I am on Mac OS X now and I want to burn it to run on a PC. If I burn the ISO for the PC on my mac will it work on a PC?

---

### Post by neptune39 on 2006-09-11
Yes it will.

---

### Post by sdubois92 on 2006-09-11
> **neptune39 said:**
> Yes it will.
thanks a bunch, gonna get to that right now.

---

### Post by p.n on 2006-10-15
i have attempted this, on my Mac but the only problem I have is that I am told that the image is too big for the disk!! Help what now?

p.n

---

### Post by aysiu on 2006-10-15
Are you following these directions?
[http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)

Also, can we assume you're using a 700 MB disk and not a 650 MB one?

---

### Post by p.n on 2006-10-15
Yip, thanks.  I eventually found the Disk Utility and that did sort the problem out.  Just one question, if my checksums fail, is it normally due to a bad download or to a bad copy to CD.  It took my more than 30 hours to download, don't really feel like re-doing it!  I am currently trying to write it to CD at the slowest possible speed to see if this will rectify my checksum problem?

Regards

---

### Post by aysiu on 2006-10-15
The checksum usually happens *before* you burn the CD, so it's probably a bad download.

A bad burn usually means you burnt the ISO too quickly.

---

### Post by p.n on 2006-10-15
Well, I ran ```
md5sum downloadfile.iso
``` and the result is the same as posted on the xubuntu download site.  Does this imply that the download is in order?

---

### Post by mips on 2006-10-15
> **p.n said:**
> Well, I ran ```
md5sum downloadfile.iso
``` and the result is the same as posted on the xubuntu download site.  Does this imply that the download is in order?

If the checksum of the downloaded file matches then I would say it is OK. Try an burn the cd at a slower speed.

---

### Post by JAwuku on 2006-10-15
You can bypass the Aqua interface altogether and open the Terminal (in the Applications/Utilities directory).

Mac OSX Unix command line has a useful command called **hdiutil**

It burns and verifies any disk image you burn (.iso or .dmg).

Just type:

```
hdiutil burn my_downloaded_distro.iso
```

for example.

---

