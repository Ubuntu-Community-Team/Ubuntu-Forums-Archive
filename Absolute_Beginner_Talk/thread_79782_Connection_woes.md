---
title: "Connection woes"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by Grimlock on 2005-10-20
Hi,
I ama Linux newbie and I am loving the product so far my only problem si those blasted BT Voyager drivers. I have installed the drivers and the synch.bin but I cannot get a data connection. I get synch no problem I can not get a data transfer here is my errors from the terminal server.

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 19
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
LCP: timeout sending Config-Requests
Connection terminated.
using channel 20
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15012), status = 0xf9
Modem hangup
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15036), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15042), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15047), status = 0xf9
using channel 21
in make_ppp_unit, already had /dev/ppp open?
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/3
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15052), status = 0xf9
Modem hangup
Connection terminated.
using channel 22
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/4
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15081), status = 0xf9
Modem hangup
Connection terminated.
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15099), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15104), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15109), status = 0xf9
using channel 23
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15114), status = 0xf9
Modem hangup
Connection terminated.
Waiting for 1 child processes...
  script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364, pid 14986
sending SIGTERM to process 14986
ERROR: failed to connect


This means absolutely nothing to me :confused: Doesn anyone have any ideas or experience of this?? It is driving me mad as I have been fiddling for hours now.

Thanks

---

