---
title: "fail installation Ubuntu live CD and alternate"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by juan75carlos on 2007-09-13
I’m having problems with the installation of Ubuntu. After trying with the Live CD it reached the point when it looks like it’s running command lines (with the black background) but after more than 36 hours it’s still doing the same thing and never stops. With the alternate desktop CD the entire installation went fine with the eject cd at the end; however when the system reboots it dies after a couple of minutes; it shows the orange progression bar but nothing happens after hours; even if I tried to boot it with recovery mode it shows the same black screen showing many commands but it dies and one point with the following line:

[240.121392] [<0104d54>]  die+0X114/0x270

This is the spec:

Dell
Intel P4 2.0 GHz
Installed System memory: 512 MB DDR SDRAM System Memory Speed 266 MHz

NVIDIA Corp VGA		IRQ  9
Intel Corp Serial Bus		11
	Multimedia		11
	Video Adapter	11
	USB		11
	USB		10
	USB		9
	USB		3
3Com Corp Network Card		11
Intel Corp Network Card		9

Ubuntu 7.04 (Fiesty) Desktop Edition (Standard personal Computer(x86 architecture). I tried everything: md5sum, burned it at 1X and checked cd for defects; I left MEMTEST86 running all night and it was OK  - No Errors

I appreciate any help you can provide me.
Thank you

SOLVED: Thanks for your help to all of you. 
It happens that the DELL Optiplex GX260 comes with a graphic card (P/N nvidia M64/32MB/PCI) which I assume it's when using Dual monitors. I remove it and it works all fine.
Thanks again.

---

### Post by jingo811 on 2007-09-13
Hmm I witnessed something similar at school once.  Where 40 identical PC's installed Feisty 7.04 at once by 40 individual persons.  Some 'puters just didn't want to work.  Might be some hardware playing tricks with you :-k

Can you install Windows on your PC?
Try some older Ubuntu distro like Dapper 6.06 or Edgy 6.10 and see if they behave the same as Feisty 7.04!

---

### Post by jw5801 on 2007-09-13
:o jingo811 has 666 beans! The devils post! :p hehe

---

### Post by PmDematagoda on 2007-09-13
Did you see if any Linux distro's other than Ubuntu worked properly?

---

### Post by jw5801 on 2007-09-13
and for a constructive post... Did you run a diskcheck on the CD after you burned it? There's an option in the LiveCD menu. It sounds like maybe the disk has corrupted.

---

### Post by PmDematagoda on 2007-09-13
> checked cd for defects

How did you check the CD?

---

### Post by juan75carlos on 2007-09-13
> **PmDematagoda said:**
> How did you check the CD?
In the main menu it shows the option for checking the CD, and I also usedWinMd5Sum

---

### Post by PmDematagoda on 2007-09-13
Did you try another Linux distro or an earlier version like Dapper or a newer version like Gutsy?

---

### Post by juan75carlos on 2007-09-14
I don't really know what' happening but I tried 6.06 6.10 and 7.04, Lice CD and alternate and they all fail from one way or another. Even if I tried in recovery mode is stops with the messge  Kernel Panic- not syncing: Fatal exception in interrupt. BUG: Unable to handle kernel paging request at virtual address FFFFd320.

I checked the CD for failures etc  but it all looks right.
Do you know if there is anything to do with the fact that it's a DELL OptiplexGX260?
Thanks in advance

---

### Post by juan75carlos on 2007-09-14
> **jingo811 said:**
> Hmm I witnessed something similar at school once.  Where 40 identical PC's installed Feisty 7.04 at once by 40 individual persons.  Some 'puters just didn't want to work.  Might be some hardware playing tricks with you :-k

Can you install Windows on your PC?
Try some older Ubuntu distro like Dapper 6.06 or Edgy 6.10 and see if they behave the same as Feisty 7.04!

Yes, I had windows before and it was OK. After formatting the HD I started installing Ubuntu (6.06, 6.10, and 7.04) with no success.
Thanks

---

### Post by jw5801 on 2007-09-14
Have a look here:
[http://www.linuxquestions.org/questions/showthread.php?t=267029](http://www.linuxquestions.org/questions/showthread.php?t=267029)

---

### Post by jingo811 on 2007-09-14
I can't think of any software based procedures or solution for your situation.  Hardwares that play tricks with you is hard to fight :(

---

### Post by juan75carlos on 2007-09-18
SOLVED: Thanks for your help to all of you. 
It happens that the DELL Optiplex GX260 comes with a graphic card (P/N nvidia M64/32MB/PCI) which I assume it's when using Dual monitors. I remove it and it works all fine.
Thanks again.

---

