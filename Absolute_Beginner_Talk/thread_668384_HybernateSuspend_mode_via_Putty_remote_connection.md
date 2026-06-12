---
title: "Hybernate/Suspend mode via Putty remote connection?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Fanatico on 2008-01-15
I wonder whether there is a way to put computer in Hybernate/Suspend mode via Putty remote connection and wake it up later at my will, again with help of Putty remote connection? I realize the answer is probably no, and this is naive question:)

Whether there is a way to put computer in Hybernate/Suspend mode via Putty remote connection for certain amount of time, let say for 4 hours, after which computer will wake up by himself and restore remote Putty connection?

Thanks

---

### Post by eckster on 2008-01-15
$ apmsleep --help
Usage:

apmsleep [+]hh:mm

Example:
   apmsleep +1:15    will suspend for one hour and 15 minutes
   apmsleep 8:00     will suspend until 8:00 am

Bugs: Daylight saving jumps are not taken into account.
      Modem ring detection may trigger early wake-up.
      Does not work with Suspend to Disk.
Bug reports to author Peter Englmaier <ppe@mpe.mpg.de>.

$

HTH

---

### Post by Fanatico on 2008-01-17
I've tried apmsleep but it said that my version of kernel doesn't support apm. Any other options?

---

### Post by zekica on 2008-01-17
If you are using ACPI (most likely), you can put your computer to sleep/hibernate but you cannot wake it up (unless it supports wake on LAN, but this is something that depends on your ethernet card and chipset).

Commands for putting your computer to sleep/hibernate are:
```
sudo pmi action sleep
```
and
```
sudo pmi action hibernate
```

---

