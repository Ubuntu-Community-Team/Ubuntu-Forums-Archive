---
title: "Setting up internet connection with B-Focus 160 usb modem"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Ancient.Dream on 2007-08-07
EDIT: Forget the old post, the problem is almost completely solved. I used minimal brute force to find a working configuration for this chipset: 
> ==== Configuration will be created with these values :

+ User : ******@IActcom
+ Password : (hidden)
+ Provider : Other
DNS 1 : 192.114.47.4
DNS 2 : 192.114.47.52
+ VPI/VCI : 8/48
+ Modem : ECI B-Focus
GS chipset : GS7470
VID1/PID1 : 0915/8102
VID2/PID2 : 0915/8102
ALT SYNCH : 5
ALT PPPOECI : 5
+ .bin file : /etc/eciadsl/gs7470_synch04.bin
+ PPP mode : VCM_RFC2364
+ use DHCP : no
+ use static IP : no

Which pretty much works, except 2 minor things:
1)My max download rate on winxp is around 305 kbps, and through a wireless connection on linux I saw synaptic managing speeds between 285 to 350, yet upon connection I can't cand download speeds higher than 210 on synaptic (from the same server). Why's there a drop of speed? Can I fix this?
2) In eciadsl-start I get the following message: 
> [EciAdsl 5/5] Setting up route table...

Waiting for ppp0...
Adding default route... SIOCADDRT: File exists
failed to set default route to ppp0 
I heard about some bug in the kernel where it doesn't assign the next availiable root if the current exists ( if I'm correct on this,I have a dial-up modem on my laptop, so it's most probably him who causes the problem...).
Does this mean I need to apply one of the kernel patches from the site?
If so, how do I apply it (still a newbie after all )?

Edit2: 
1)to solve this prob, simply use some other synch.bin, usually creating one yields the best results (not always). There're instructions on the main site that explain how to create a synch file.
2) If the internet works, ignore it. Otherwise go to the eciadsl forums
and read the posts in a similar thread. 

Here's the old post for reference for those, who are interested: 
> Hi all!

I'm new to ubuntu and  can't get to connect using this modem.
After some search work, I found out that my modem is ECI Globalspan Virata B-Focus 160 and about eciadsl and pppoe, but couldn't get them to work.
Pppoeconf couldn't find my modem and after I installed eciadsl-usermode_0.11-1_i386_with_synch_patch.deb and upon configuring, I got the following problems:
[quote]maximk@Midnight:~$ sudo eciadsl-probe-synch

WARNING: if no /etc/eciadsl/eciadsl.conf file exists,
default VID/PID will be assumed. This eciadsl.conf file is generated using
eciadsl-config-tk or eciadsl-config-text, please read the INSTALL file to
properly install and configure the driver
This script requires your modem to be supported by the driver, and that
you've installed some extra synch .bin (the official synch_bin package for instance)
It might be also necessary to unplug/wait/replug your modem before your
this script and to ensure that no pppd/eciadsl-pppoeci instance is running


Config read from /etc/eciadsl/eciadsl.conf

Type in a directory where to find the synch .bin
[default is /etc/eciadsl]: /etc/eciadsl

These synch .bin will be tested:
synch18.bin
synch26.bin
...
synch55.bin
Start the tests now? (Y/n) y

Loading firmware..
*** failed to load firmware, aborting

> maximk@Midnight:~$ eciadsl-doctor
You need to be root (type su)
maximk@Midnight:~$ sudo eciadsl-doctor
You are using linux kernel version 2.6.20-16-generic
Support for USB is OK
Preliminary USB device filesystem is OK
dabusb module is not loaded: OK
UHCI support is OK
OHCI support is not needed
/dev/ppp is OK
HDLC support is OK
HDLC support is OK (no bug)
You are using pppd version 2.4.4 (untested)
No existing PPP connection... trying to make one (please wait)
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Modem hangup
Connection terminated.
Script /usr/bin/eciadsl-pppoeci -vpi 8 -vci 48 -vendor 0x0915 -product 0x8102 -mode VCM_RFC2364 finished (pid 6427), status = 0xf5
using channel 2
...
using channel 10
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Modem hangup
Connection terminated.
Script /usr/bin/eciadsl-pppoeci -vpi 8 -vci 48 -vendor 0x0915 -product 0x8102 -mode VCM_RFC2364 finished (pid 6682), status = 0xf5
PPP: very bad ... usermode driver just crashed
tail: Warning: "+number" syntax is deprecated, please use "-n +number"

> maximk@Midnight:~$ sudo eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Warning: firmware seems to be already loaded
Check that your modem is OFF before running eciadsl-start (if modem is
powered on, then unplug/replug it)

[EciAdsl 3/5] Synchronization...

 ERROR reading interrupts                              
ERROR eciadsl-synch SYNCHING: failed                                     
ERROR eciadsl-synch: failed                                                         
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 11
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Modem hangup
Connection terminated.
Script /usr/bin/eciadsl-pppoeci -vpi 8 -vci 48 -vendor 0x0915 -product 0x8102 -mode VCM_RFC2364 finished (pid 6874), status = 0xf5
...
Connection terminated.
using channel 20
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Script /usr/bin/eciadsl-pppoeci -vpi 8 -vci 48 -vendor 0x0915 -product 0x8102 -mode VCM_RFC2364 finished (pid 7085), status = 0xfb
Modem hangup
Connection terminated.
ERROR: failed to connect

> maximk@Midnight:~$ sudo eciadsl-config-text

===== Welcome to the EciAdsl Linux driver configuration =====

At any time, press Ctrl+C to quit this script without saving modifications.

Tip: you can run eciadsl-config-text with a .bin file as parameter to change
your .bin quickly.

Your choice:

1) Configure all settings
2) Remove dabusb module
3) Change synch .bin file

Enter your choice (1-3, default is 1): 2

Please unplug your modem and then press ENTER

dabusb is not loaded
no hotplug blacklist support detected or hotplug not installed?


> maximk@Midnight:~$ sudo eciadsl-firmware
can't find your EZUSB USB ADSL Loader
ERROR eciadsl-firmware: failed
eciadsl-firmware: success



> maximk@Midnight:~$ sudo modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a 
rm: cannot remove `/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/dabusb.ko': Permission denied
 

Can anyone help me figure out what all this means, and how to deal with it?

It turned out on windows, the dialer installer chooses rfc 2516- PPPoE Encapsulation. Does this mean the chipset is unsupported by eciadsl?

Anyway, If anyone here knows any alternative solution, please be kind and post.   :)[/QUOTE]

---

