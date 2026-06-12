---
title: "Slow Responsiveness cuz swap is too big?"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by mxiong on 2005-09-26
Help neeed!

I just installed Ubuntu 5.10 "Breezy" Preview Release. The biggest problem right now is that the Ubuntu system is slower compared to XP on my very same laptop. During the setup I used the guided (automatic) partitioning and the swap partition was set to 1.5GiB (My RAM is only 512MB) by default, and I didn't change it. Then I found out the swap should only be 1-2 times in size of the RAM. So is the slow responsiveness because my swap was set too large? If it is the case, how can I change the size of /swap without totally reinstalling the Ubuntu?

Thanks in advance for any advice.

---

### Post by az on 2005-09-26
[QUOTE=mxiong]Help neeed!

I just installed Ubuntu 5.10 "Breezy" Preview Release. The biggest problem right now is that the Ubuntu system is slower compared to XP on my very same laptop. During the setup I used the guided (automatic) partitioning and the swap partition was set to 1.5GiB (My RAM is only 512MB) by default, and I didn't change it. Then I found out the swap should only be 1-2 times in size of the RAM. So is the slow responsiveness because my swap was set too large? If it is the case, how can I change the size of /swap without totally reinstalling the Ubuntu?

Thanks in advance for any advice.[/QUOTE]
The preview release was a little sluggish.  A few days later, after som updates, things started to get better.  A current system (if you dist-upgrade, or just get all your updates from the net) should make your system as snappy as it normally should.

Also, perhaps you should install a 686 or k7 kernel.  They are optimised for intel or amd processors, respectively.

By and large, I find Ubuntu to be faster than Windows XP.

And no, a larger swap does not mean that the swap will be used preferentially.  The kernel will swap only as a last resort.

---

