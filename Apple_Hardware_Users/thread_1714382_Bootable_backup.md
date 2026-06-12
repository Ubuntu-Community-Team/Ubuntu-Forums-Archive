---
title: "Bootable backup?"
date: 2011-03-25
forum: Apple Hardware Users
---

### Post by B_Free on 2011-03-25
Once installed (any version), you have everything working properly, can you make a bootable back up to that drive?

---

### Post by DarkTide on 2011-03-26
I think it's possible ;)

---

### Post by linuxopjemac on 2011-03-26
dd it
[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

---

### Post by B_Free on 2011-03-27
What does dd mean?
OK. Went to that link. In essence, I'm trying to make an install version for a particular Mac. The benefit of having an old Mac is "They aren't making any new hardware for them". We don't need the installer looking for something that isn't there. The Macs worked so well because the software and hardware were made for each other. Linux tries to be everything to everybody. That's great if it works. But by reading these forums for nearly 2 years now, the questions still remain the same.
oswaldkelso and linuxopjemac seem to be authorities on many Linux subjects. So, I'd like to ask them, can you make an install disk from an existing, perfectly running PPC? Have an install disk for an iMac G3, one for a B&W G3, etc.
And if so, how?
Support for PPC software is to be cut in October 2011. oswaldkelso, will Debian still support PPC?

---

### Post by linuxopjemac on 2011-03-28
Debian supports most ancient PowerPC based Macs, also the B&W's. Due to some stupid bug Ubuntu cannot be easily installed on the B&W. I am sure that Debian Squeeze is your solution to all your old G3 Macs. You don't need to make installers for each Mac separately.

dd copies the content block by block. So basically you get a clone of a hard drive if you do that.

I experimented with simple-cdd on a PowerPC Debian system to make installers from an existing system. I could never get it done, so I gave up. That was in the time that Squeeze was not stable yet. It might have changed by now, I don't know. As I could not get it to work, I was not able to provide an iso based installer for MintPPC. The latter would have been so much easier for people to install MintPPC.

---

### Post by B_Free on 2011-03-28
So, if you make a back up of your hard drive, if something goes wrong, how do you re-install it? Do you have to re partition the disk? Do you erase and re-install?
What I'm hinting at is, if you install, let's say, MintPPC on an iMac G3, dd it, and used it to install to any and all iMac G3s, is that possible? The install would be a clone of your computer. Give a password and user name that the recipient would change.

---

### Post by linuxopjemac on 2011-03-28
That's theoretically possible, provided that the hard drives are of equal size. I have never tried it though.

---

### Post by B_Free on 2011-04-03
When you made MintPPC, don't you replace parts of the Debian release you first install with your files? Or when you update any distro, they replace files with new? Hope that didn't sound weird!

---

### Post by linuxopjemac on 2011-04-04
A part of the files are replaced by my own. For the most part it's Debian. The small repository of MintPPC I upgrade myself (source code). The rest is upgraded via the Debian repositories.

---

