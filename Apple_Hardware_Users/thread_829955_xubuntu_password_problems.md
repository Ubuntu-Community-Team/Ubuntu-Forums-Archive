---
title: "xubuntu password problems"
date: 2008-06-15
forum: Apple Hardware Users
---

### Post by collarfor12 on 2008-06-15
i recently bought an imac G3 for £10 with xubuntu installed on it, but theres one problem

theres a username and password to get on an i have no idea what it is as i got it at a yard sale!


any help cracking the pass/installing fresh OS?

thanks

---

### Post by cyberdork33 on 2008-06-15
reinstall?

---

### Post by stream303 on 2008-06-15
The good news is that you know it will work.

I'd definitely do a reinstall, but perhaps instead of spending time trying to get around the old passwords, would be to download an "alternate" install image, and use that to wipe the drive clean of old cruft with a method such as using dd.

Then reinstall.

---

### Post by collarfor12 on 2008-06-15
i tried installin kubuntu from disk, but it just booted xubuntu, 

can someone link me to a tut on how to install it from the boot menu?

---

### Post by stream303 on 2008-06-16
Ok, looks like you are aiming for a total reinstall.

Before you begin, what iMac do you have, and how much ram is on-board?  Even though Xubuntu seems to be running on it, it may not be doing so very well, and might be the reason for the sale. :)

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Is your hard drive original, or is it a replacement that might be larger than oem specs?  Some early G3's had 8gb or 128gb partitioning limits for the root partition.

It is also helpful to know which version of Ubuntu you are trying to install.  Here is a convenient link to the downloads:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

If you are bandwidth or time-limited, you may find the minimal-iso, or netinstall type images a better deal:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Most recommend the "alternate" image for the least amount of hassle, but if you have enough ram, the live-cd *may* work.

Be sure you burn the image as an iso (not just copied over), onto CD-R and not CDRW media, and at a low speed, say 2x or 4x.  Boot the CD by either holding down the "C" key when powering up, or power up and hold down the "C" key very quickly afterwards.

If this is a total dedication to the machine, just allow guided partitioning to use the whole disk.

These two faqs are going to be very handy:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Give this a go - but it is vital to get the amount of ram you have onboard so you don't end up wasting too much time.  If you don't know any specs, you can just try to install and we can take it from there.

You can see that this probably won't be a "drop-in" install. :)

---

### Post by collarfor12 on 2008-06-16
no idea on the specs as i cant get onto the machine :(

its an iMac G3, blue slot loading, thats all i know

the HDD has been replaced though, as its very quiet and the stock ones are very loud (i belive)

---

### Post by stream303 on 2008-06-16
Ok, I guess you'll just have to try it and see what turns up.  It is good to know about that hard drive, since early iMacs sometimes have an 8gb partitioning limit (keep it at 7gb to be totally safe) so custom partitioning may be in order.

---

