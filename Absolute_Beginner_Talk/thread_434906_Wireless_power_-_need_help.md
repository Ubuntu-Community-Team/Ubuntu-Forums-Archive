---
title: "Wireless power - need help"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by andrew01 on 2007-05-06
Hello,

I trying to change a tx-power on Intel Pro Wireless 2100 card with that command:

sudo iwconfig eth1 txpower 1

but it doesn't work. I always have Tx-Power:16 dBm

What I am doing wrong? 

I also have strange output for command:

iwlist eth1 txpower

which is:

eth1      unknown transmit-power information.

          Current Tx-Power:16 dBm       (39 mW)

Thank you for any help.
Andrew

---

### Post by enigma007 on 2007-05-07
There is no such thing as wireless power.

---

### Post by enigma007 on 2007-05-07
Just kidding i don't know how to fix your problem.

---

### Post by jmendez2 on 2007-05-07
Try making sure that '1' is a valid variable by pulling up a list of the available parameters.
This might help also;   [http://www.linuxcommand.org/man_pages/iwconfig8.html](http://www.linuxcommand.org/man_pages/iwconfig8.html)

Good Luck.

---

### Post by andrew01 on 2007-05-08
I did 

iwlist eth1 txpower

but unfortunately the output was:

eth1 unknown transmit-power information.

Current Tx-Power:16 dBm (39 mW)

Is that mean that ipw2100 doesn't support such a thing
like changing txpower ??

---

