---
title: "No legacy HD support means I can't install Linux?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-08-07
I found the perfect laptop to fit my needs but I found a review saying that Legacy isn't supported by the BIOS. In general, the BIOS was said to be really bad too. Here is a quote from another for the **HP dv2500t Notebook**.

"A small note for people that want to install Windows XP on this laptop, my BIOS version is F.05, and is missing the option for legacy support for the SATA HD. I tried using a Windows XP Pro SP2 CD and no HD was detected in the setup process, I have yet to try nLite to create a custom boot disc, but Intel drivers are available for use in creating such a boot disc.  Also HP has no drivers listed for Windows XP and the DV2500t, but most drivers are readily available from the HP site and via the power of Google."

Is this a hardware thing, or can I get software to fix this. This is a huge disappointment and I might even call HP about it, I was happy with everything about it until just now. :(

PS: I browsed HP's site and found a BIOS update, but it doesn't add legacy support.

---

### Post by kavon89 on 2007-08-07
Dang, I found some info about the dv6500t, which uses the same BIOS and hardware (for the most part).

[http://www.nogodforme.com/HPDV6500T.htm](http://www.nogodforme.com/HPDV6500T.htm)

He has to do some slip stream stuff for XP with nLite, his sound doesn't work, and the drive is messed up. Not to mention he has to use the alternate CD to install.

Looks like HP and Ubuntu don't get along. :/

---

### Post by asmoore82 on 2007-08-07
hmm... you may just need to install Linux and then boot with the kernel on the Live CD ...

after linux is install boot from the live CD again and change the boot line to something like ...

```
vmlinux.... root=/dev/sda1 ....
``` and you will load the Kernel from the CD but the OS
from the Hard drive and then never reboot
... which Linux is good at anyway ;)

---

### Post by Inxsible on 2007-08-07
> **kavon89 said:**
> Looks like HP and Ubuntu don't get along. :/

I would have to disagree. I use Ubuntu on my dv9000t and have had no problems whatsoever. Anything I throw at it, it just works out of the box until now.


Scratch that....the integrated webcam doesn't work :( ...but I can live with it

---

### Post by kavon89 on 2007-08-07
I guess I'll get the Inspiron 1420. The 1420 with Ubuntu installed has Integrated graphics, so I'm getting the vista one with a 8400 GS and wiping the drive.

---

### Post by mooseboy on 2007-08-09
Linux has supported SATA natively for quite some time. This note you came across is talking about emulating the SATA hard drive to make it look like an IDE drive. This is not necessary for the HP x500t laptops to work under Linux. 

In short, your hard drive will work fine under Linux.

---

