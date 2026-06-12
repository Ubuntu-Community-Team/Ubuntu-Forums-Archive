---
title: "connecting via a modem"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2007-12-10
i went to an ISP an paid for an internet service but i could not connect it the phone to my ubuntu  gusty it says:

pradeep@pradeep-laptop:~$ sudo wvdialconf
[sudo] password for pradeep:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
pradeep@pradeep-laptop:~$ 

but wheni used my friends windows xp system it detected it and installed it, actually it is a nokia phone i connect via usb

pls help me urgent

---

### Post by Shinbu-Otaku on 2007-12-13
have you tried installing it under System>Administration>Network, because it looks like you are installing it under the terminal. With Network it is basically a point and click approach, and i've never had a problem with any form of network using that.

If you have tried this already, it could be that your modem is not linux compatible, as they are obviously mostly made for windows.

Hope that helps

---

