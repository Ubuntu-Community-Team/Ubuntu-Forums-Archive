---
title: "Can't install 10.04 on a iMac 27&quot; i7"
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by jisaac on 2010-04-17
It seems that there is no "safe graphic mode" or similar when running the live cd.

I only get a blank screen.

Any idea?

Thanks.

---

### Post by binary10 on 2010-04-17
Try this :

Bug still appears in Beta2, on my iMac11,1 i7 -

 I had to do a f6, esc, (selecting nomodeset doesn't appear to change the line) then manually added the following in the boot line:

   radeon.modeset=0 nomodeset

It's what I did to get the 10.04 on my iMac 11,1 (27") i7 

 see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660)

---

### Post by jisaac on 2010-04-17
Thanks!

I'm replying from my new lucid lynx beta2 live cd session!

---

### Post by binary10 on 2010-04-17
No problems, as you can see from the bug report it took me a couple of attempts to get the right option and hopefully it'll be uprev'd in the final build.

Just wish I could get my usb external boot going next.

---

### Post by B_Free on 2010-04-18
radeon refers to .....? In older machines what might you type? Say an iMac 266 PPC.

---

### Post by binary10 on 2010-04-23
As you've reported, this is broken again with the RC of 10.04.

Looking for workaround again.

---

### Post by jisaac on 2010-04-23
You're right! I've just marked this thread as unsolved :(



---
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660)

---

### Post by binary10 on 2010-04-27
found that non mac users reporting issues and resolutions with ATI HD5xxx.

I've not tried it on my iMac11,1 yet but I thinking how can we even get to that stage to install. 

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/560306](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/560306)

---

### Post by jisaac on 2010-05-01
I've painfully installed "10.04 Final" using Beta2 and doing a full update :(

It's clearly not the way to do it but this is the only one I've found :(

---

### Post by ampted on 2011-08-19
> **binary10 said:**
> Try this :

Bug still appears in Beta2, on my iMac11,1 i7 -

 I had to do a f6, esc, (selecting nomodeset doesn't appear to change the line) then manually added the following in the boot line:

   radeon.modeset=0 nomodeset

It's what I did to get the 10.04 on my iMac 11,1 (27") i7 

 see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660)

f6 + nomodeset works...

---

