---
title: "[SOLVED] printer disappears from printer list"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by dckirba on 2008-02-01
Hello all,

with some good help and nudges in the right direction, a couple of us have got an HP printer set up on a dapper machine at work. The printer works well and is shared on a network of macs and everything is hunky dory.

After I got back from a meeting today, the computer was stuck and not responding so I manually restarted it. Checking the system log, I found this:

```
Feb  1 15:53:22 localhost python: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256 
Feb  1 15:53:23 localhost python: hp-toolbox[4820]: error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256
Feb  1 15:53:23 localhost python: hp-toolbox[4820]: warning: Device not found
Feb  1 16:00:12 localhost python: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256 
Feb  1 16:00:13 localhost python: hp-toolbox[4820]: error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256
Feb  1 16:00:13 localhost python: hp-toolbox[4820]: warning: Device not found
Feb  1 16:01:27 localhost python: hp-toolbox[4820]: error: Printer list empty
Feb  1 16:04:48 localhost python: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256 
Feb  1 16:04:49 localhost python: hp-toolbox[4820]: error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256
Feb  1 16:04:50 localhost python: hp-toolbox[4820]: warning: Device not found
Feb  1 16:05:52 localhost python: hp-toolbox[4820]: error: Printer list empty
Feb  1 16:10:32 localhost python: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256 
Feb  1 16:10:34 localhost python: hp-toolbox[4820]: error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256
Feb  1 16:10:34 localhost python: hp-toolbox[4820]: warning: Device not found
Feb  1 16:12:35 localhost python: hp-toolbox[4820]: error: Printer list empty
Feb  1 16:16:53 localhost python: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256 
Feb  1 16:16:56 localhost python: hp-toolbox[4820]: error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256
Feb  1 16:16:56 localhost python: hp-toolbox[4820]: warning: Device not found
Feb  1 16:18:04 localhost /USR/SBIN/CRON[17815]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  1 16:18:41 localhost python: hp-toolbox[4820]: error: Printer list empty
Feb  1 16:24:17 localhost python: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256 
Feb  1 16:24:18 localhost python: hp-toolbox[4820]: error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_P2015_Series?serial=00CNBW77H256
Feb  1 16:24:18 localhost python: hp-toolbox[4820]: warning: Device not found
Feb  1 16:25:56 localhost syslogd 1.4.1#17ubuntu7: restart.
```

So I assume the printer just popped off the list? I found a similar thread but the problem in that case was that the printer was off when the system started and then it wouldn't be recognised.

How can this be remedied? The printer is HP p2015, system is Dapper. Everything works fine on restart.

Thanks for your help,
Cheers,
David K

---

### Post by smacattack on 2008-02-01
this might sounds dumb... but you didn't change the USB port it was in eh?

---

### Post by dckirba on 2008-02-01
:)
Unfortunately no. I left for a couple of hours and came back. No one else touched it.Maybe I should just wait and see if the same thing happens again.

---

### Post by dckirba on 2008-02-01
I just realised it may be an overload on the USB port. There is only one functional USB 1.1 port on this machine. Printer, keboard and mouse going through it>

Have substituted with older mouse and keyboard and now only have the printer on the USB. Will see if this does the trick.

Cheers

06/02
Yes, that was the problem. Printer's been on since then, no problems  :)

---

