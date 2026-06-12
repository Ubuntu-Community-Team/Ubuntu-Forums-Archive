---
title: "the sat. card prevent boot of the linux"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by totti10it on 2007-06-24
i have SATELLITE CARD ( pci card)
 :TWINHAN vision plus     1020 A  ( red color with normal -old- tuner ) 

 when the cars is connected no linux distro. can boot i tried several distros livecd's and normal but none of them could ever boot .each distro is stopped at a step of detection of hardware.when i removed the card all distros could boot normally live cd's worked well and normal distros's i could install well ..so pls wht is the solution.. i'm windows user and i want to swich to linux but i'm still beginner and i can't do without my sat. card and it's impossible each time i need to use linux i 'll remove the card from pci slot

thanx everybody and waiting 4 ur help

---

### Post by DrClaw27 on 2007-08-27
I'm having the same problem and have had no luck finding a fix.

---

### Post by lowmax on 2007-10-01
Exact same problem over here too.

---

### Post by dwhitney67 on 2007-10-01
Here's a [link]("http://members.optushome.com.au/jhonan/dst/") to some info that might help you.  Read the "txt" files for details.

---

### Post by rosponius on 2008-03-19
I have a dexatek sphere dk-5701 and the same problem you have:

I added the following lines in this file: etc/modprobe.d/options (thanks to an italian ubuntu forum user who suggested this solution for a twinhan card, it works also for my dexatek):

options dvb_core dvb_shutdown_timeout=0
options bttv i2c_hw=1 card=0x71

Don't know what they means, dont' know if the card works (I didn't try yet) but at least now I can boot my ubuntu!:)

---

