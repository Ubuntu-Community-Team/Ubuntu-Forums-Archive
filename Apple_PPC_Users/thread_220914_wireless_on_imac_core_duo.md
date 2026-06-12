---
title: "wireless on imac core duo"
date: 2006-07-22
forum: Apple PPC Users
---

### Post by jakemikey on 2006-07-22
Hi all, 

I've followed the onmac tutorial on getting a triple-boot Intel iMac up and running and I can successfully boot into all three OSs.  Now I'm having trouble getting wireless on my iMac Core Duo up and running.  There doesn't seem to be much documentation on this (at least I haven't been able to find any).  It's been really frustrating because I've read of other people getting both wireless/bluetooth working, but then they don't explain how!

Can anyone help me or tell me where to look?  Thanks!

---

### Post by chasisaac on 2006-07-28
Check out. 

[http://www.ubuntuforums.org/showthread.php?t=142727&highlight=airport+exact](http://www.ubuntuforums.org/showthread.php?t=142727&highlight=airport+exact)

---

### Post by jakemikey on 2006-07-28
Thanks  - I tried following a similar bcm43xx howto with no success.  Ndiswrapper has been the only thing that has gotten me consistent, working wifi on all my machines.  I tried ndiswrapper 1.13 from source with the drivers installed on my Windows partition from the boot camp CD.  That finally worked!  Let it be known here: instructions for wifi on Macbooks/Macbook Pros WILL NOT work with the iMac Core Duo - they use totally different wifi chipsets.  For the iMac Core Duo use ndiswrapper and the bcmwl5 inf/sys files supplied by the boot camp CD.

Anyway...now if I could just get sound  working I'd be in business.

---

### Post by chasisaac on 2006-07-30
> **jakemikey said:**
>   Let it be known here: instructions for wifi on Macbooks/Macbook Pros WILL NOT work with the iMac Core Duo - they use totally different wifi chipsets.  For the iMac Core Duo use ndiswrapper and the bcmwl5 inf/sys files supplied by the boot camp CD.
.

This is good to know. Thank you for reporting back

---

