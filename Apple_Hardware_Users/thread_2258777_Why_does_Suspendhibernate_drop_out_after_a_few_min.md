---
title: "Why does Suspend/hibernate drop out after a few minutes in Lu 14.04?"
date: 2014-12-30
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-12-30
I found an old thread here where I posted about problems in 12.04 with "failure to suspend" but really got no response to the problem then and the problem continues in 14.04.  A bug report has been filed, and status is "confirmed" but that is about the extent of it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366624)

Lately when I put the iBook into hibernate . . . and, as I routinely do in  OSX, I unplugged the computer . . . a few minutes later the computer  dropped out of hibernate and powered down . . . requiring cold boot to  get back into GUI . . . problem continues in spite of the suggestion  provided in LP Answers to increase my swap partition . . . which I went to 1.75x of RAM to approx. 1 GB of swap.

The  situation did improve as far as short term suspend/hibernate goes . . .  but, the problem is not solved.  Looking for some further insight I posted this on my question:

 "["My last question remains, what would be the recommended minimum  swap that will still provide "suspend" or "hibernate"??? 1x RAM? I have  640MB and the installer set it to something like 526 MB swap . . . so  less than 1x did not work . . . would 1 or 1.5x get it? 1.25x?? Or 2x  would give me a cool running "suspend" that would zip in and out of  itself?"]


 Was waiting to do some more testing with the increased RAM . . . as I  stated previously, the situation is "improved" with the added swap, but  the problem is ***not solved**** . . . just "answered."
 ."

 Anybody else have this issue with suspend/hibernate in 14.04 and/or PPC hardware?  Please add your name/computer to the bug report.

The earlier threads:

[http://ubuntuforums.org/showthread.php?t=2146699&highlight=failure+revive+suspend](http://ubuntuforums.org/showthread.php?t=2146699&highlight=failure+revive+suspend)

[http://ubuntuforums.org/showthread.php?t=2059610&highlight=failure+revive+suspend](http://ubuntuforums.org/showthread.php?t=2059610&highlight=failure+revive+suspend)

e.e.p.

---

### Post by rican-linux on 2015-01-07
Do you have KMS enabled (I think it is on be default on 14.04)? KMS has been known to break suspend and hybernate.

---

### Post by este.el.paz on 2015-01-07
> **rican-linux said:**
> Do you have KMS enabled (I think it is on be default on 14.04)? KMS has been known to break suspend and hybernate.

@rican-linux:

Thanks for stopping by, since I've posted this I've moved to a UbuntuMATE install, but, in Lu 14 it did improve the situation by expanding the swap . . . which I carried over to MATE . . . in Lu, there was both hibernate & suspend but it did not maintain once the computer was unplugged.  Now in MATE it's less "responsive" to the "suspend" command . . . .  But, yes, in order to keep the desktop from freezing in Lu 14.04 I went with boot params "video=ofonly radeon.agpmode=-1" . . . so I've carried that over to MATE.  There is a bug report, but it hasn't garnered any response from an actual human triager . . . .

e.e.p.

---

### Post by rican-linux on 2015-01-07
I tried MATE on Debian Jessie for a bit. How has your experience on MATE been? I felt I got better performance on LXDE.

---

### Post by este.el.paz on 2015-01-07
> **rican-linux said:**
> I tried MATE on Debian Jessie for a bit. How has your experience on MATE been? I felt I got better performance on LXDE.


r-l:

I like MATE, on my MBPro I tried a few flavors of LM and found the MATE edition ran better than Cinn.  There are more features with the MATE DE, and possibly that might put some load on the PPC, but then so does straight Ubuntu which is considered a little heavier on hardware.  LXDE is lighter, therefore faster . . . but, then, usually less "features" or less eye candy.  I think MATE is "newer" than LXDE, so maybe some general upgrades on function, file manager stuff . . . .

e.e.p.

---

### Post by rican-linux on 2015-01-07
You dual booting your MAC with OS X and Ubuntu?

---

### Post by este.el.paz on 2015-01-07
> **rican-linux said:**
> You dual booting your MAC with OS X and Ubuntu?

Yes.

---

