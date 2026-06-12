---
title: "Strange ata errors"
date: 2011-08-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by neojames on 2011-08-31
For a little while now, I've been getting strange errors on my Desktop computer during bootup and everything is running significantly slowly, for instance login from cold takes about 10 min, but when I logout then back in it does it in <1 min. Here is a output from dmesg which is similar to the bootup one:

```

[ 1316.602968] ata2.00: status: { DRDY ERR }
[ 1316.602971] ata2.00: error: { ICRC IDNF ABRT }
[ 1316.602982] ata2.00: hard resetting link
[ 1316.950022] ata2.01: hard resetting link
[ 1317.460079] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1317.460094] ata2.01: SATA link down (SStatus 0 SControl 300)
[ 1317.500268] ata2.00: configured for UDMA/33
[ 1317.500416] ata2: EH complete

```

The actual bootup one is slightly different and mentions an exception emask and failed command READ DMA EXT.

The spec of my computer is a ASUS P5QL/EPU motherboard, two SATA HD's and a SATA drive. My Ubuntu install is one the first drive with the home partition split on that drive and the other drive has a Windows XP install which does not experiance any problems, except the normal windows ones :P

I have Natty on it, which I installed over my previous Lucid install keeping only the home partition as well if that matters and also the old installs home folder is separate to my current installs.

Here is my uname -a output just to be on the safe side!

```

Linux GLaLINUX 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Thank you for any help :)

---

### Post by neojames on 2011-09-19
After doing a reinstall (unrelated) the problem still persists but login etc is a little faster (less stuff to load I presume).

---

