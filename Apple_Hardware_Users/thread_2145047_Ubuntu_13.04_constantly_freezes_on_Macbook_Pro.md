---
title: "Ubuntu 13.04 constantly freezes on Macbook Pro"
date: 2013-05-14
forum: Apple Hardware Users
---

### Post by catsy on 2013-05-14
I recently installed 13.04 as a dual boot on my mid 2010 macbook pro and it freezes after about 20 minutes to an hour of use, making it pretty much impossible to get any actual work done. First the graphics on one part of the screen will break, then the entire screen, and whatever music may be playing will keep playing about the same second over and over again, and the mouse may move but it will do so very slowly and jerkily and I have to shut down the computer. I was trying to look things up and people said a soft reset instead of a hard reset would be better in this case, but I don't have all of the keys required. I thought maybe the laptop was overheating so I put in tlp, but that didn't fix the problem. OSX very occasionally has problems overheating but it's nothing like this. Is there any way to fix this? :confused: I would like to actually be able to use ubuntu!

---

### Post by 2F4U on 2013-05-14
The first thing to do would be to look into the system log files directly after such a problem happens. It might give some hint on what goes wrong. Besides that, it might also be useful if you could post your hardware configuration and whether you are using proprietary graphics drivers.

---

### Post by catsy on 2013-05-14
I'm using a proprietary graphics driver. I mean it's the defaults for a mid 2010 macbook pro: 2.4 GHz Intel Core 2 Duo processor, 4 GB 1067 MHz DDR3 memory, NVIDIA GeForce 320M 256 MB graphics whatsit, except for I recently installed a new hard drive (I installed 13.04 after I installed the hard drive). Where would I find the log files? Through Terminal or is there something like Console on ubuntu?

---

### Post by Jrgc on 2013-05-16
To see the log, you may use the "System Log" viewer (search for "log" in the launcher and it will show up). Another way to monitor potential power consumption anomalies could be to instal powertop. This will show you what's going on in details.
I have ubuntu 13.04 running on my MBP (2008 version) and do not face such kind of problem, but I'm ready to help.

---

### Post by catsy on 2013-05-16
How can I tell when I reboot? Is it at [0.00000]?

It really doesn't help that the logs seem to be white on white... arg.

It seems to be freaking out right now and I'm getting:

May 16 13:08:12 SBURB-Beta kernel: [  878.596155] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596159] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 0 class 0x0030 mthd 0x0238 data 0x00000000
May 16 13:08:12 SBURB-Beta kernel: [  878.596168] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596172] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 0 class 0x0030 mthd 0x023c data 0x00000000
May 16 13:08:12 SBURB-Beta kernel: [  878.596180] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596183] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 0 class 0x0030 mthd 0x030c data 0x20a903c3
May 16 13:08:12 SBURB-Beta kernel: [  878.596192] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596195] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 0 class 0x0030 mthd 0x0310 data 0x43690000
May 16 13:08:12 SBURB-Beta kernel: [  878.596204] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596207] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 0 class 0x0030 mthd 0x0234 data 0x00000000
May 16 13:08:12 SBURB-Beta kernel: [  878.596217] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596221] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 0 class 0x0030 mthd 0x031c data 0x00000450
May 16 13:08:12 SBURB-Beta kernel: [  878.596229] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596233] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 2 class 0x502d mthd 0x0320 data 0x000002c5
May 16 13:08:12 SBURB-Beta kernel: [  878.596242] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596246] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 2 class 0x502d mthd 0x0324 data 0x00000101
May 16 13:08:12 SBURB-Beta kernel: [  878.596254] nouveau E[  PGRAPH][0000:04:00.0]  ILLEGAL_MTHD
May 16 13:08:12 SBURB-Beta kernel: [  878.596258] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 2 class 0x502d mthd 0x0328 data 0x00000000
May 16 13:08:39 SBURB-Beta kernel: [  906.289840] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR INVALID_VALUE
May 16 13:08:39 SBURB-Beta kernel: [  906.289847] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May 16 13:08:39 SBURB-Beta kernel: [  906.289852] nouveau E[  PGRAPH][0000:04:00.0] ch 2 [0x000fb2a000] subc 7 class 0x8697 mthd 0x0e04 data 0x00044110

However it has not actually frozen yet. The graphics are just very broken.

---

### Post by catsy on 2013-05-20
I am still having trouble with this! Please help if you can.

---

### Post by Kynolin on 2013-05-27
I had this exact same issue with frequent 3-7sec freezing on my 2010 MacBook Aluminium (pro) 2.4GHz. I *have* upgraded to 8GB of RAM and an SSD, just FYI, but the freezing is still there and very annoying. From some of my notes I had from fighting with the same issue in 12.10, there were two things I remember that might help.

The first two things I did from my notes after a clean install:

1)
Apport constantly errored for me in 12.10, and this is how I fixed it. I'm not sure if it's related to anything in 13, but it's the only other thing I did to the system after a clean install before step 2, so I want it documented in my post.[INDENT]sudo apt-get purge apport[/INDENT]
[INDENT]sudo apt-get autoremove[/INDENT]
[INDENT]sudo apt-get clean[/INDENT]
[INDENT]sudo apt-get install apport[/INDENT]
2)[INDENT]sudo apt-get install nvidia-experimental-310[/INDENT]
[INDENT]reboot[/INDENT]

Those being the only two config changes, my freezing seems to be gone on the Mac now. From what I remember, I had to do a lot more in 12.10 to get the nvidia 310 drivers working, but it seems to be going great after those simple steps. Now.. if only I could find my lost notes on the WiFi driver fix. blah..

I'm not sure if something with the generic Ubuntu drivers causing issues, but I remember my Mac being nightmarish in 12.10 until I got the Nvidia 310 working properly. Unfortunately, my detailed notes are backed up somewhere I can't remember, as all my 12.10 config was done while on vacation last year.

Hope this helps!:p

EDIT: Nvidia Proprietary 310 drivers seem to mess up the brightness up/down keys. I do not have a solid solution or link on how to fix yet.

---

### Post by catsy on 2013-05-28
All right, I tried your fix. Thus far I've had no freezing. We will see how long this lasts...

---

### Post by Way310 on 2013-05-28
Try booting on unetbootin! it worked for me for  Bypassing error 15!:p Hope This helps! enjoy!

---

### Post by GhettoMrBob on 2013-05-31
I'd skip the experimental drivers and use the proprietary, tested one. 

To get the brightness control back you need to edit your xorg config:

sudo gedit /etc/X11/xorg.conf

Look for Section "Device" with details about Nvidia. In that section add the lines:
Option "RegistryDwords" "EnableBrightnessControl=1"

Save and reboot. You're proprietary graphics should now work without artifacts/lockup and you should be able to control the brightness

**Edit:**
Attached a screenshot of my config. Just ignore the other settings, the highlighted one is the one you want.

---

### Post by troutinthemilk on 2013-06-12
I had similar problems when I installed 13.04, so I went back down to 12.10. Has any of the above worked for you to fix 13.04?

---

### Post by Kynolin on 2013-07-02
> **troutinthemilk said:**
> I had similar problems when I installed 13.04, so I went back down to 12.10. Has any of the above worked for you to fix 13.04?

The steps I took are still working flawlessly on 13.04 to this date, even after a few apt-get upgrade's. I'm not running into errors or anything either, just a great Ubuntu experience. I have been too lazy to fix the brightness still, as I'm always plugged in. The old battery only gets max 2hrs anyways. XD

To clarify, I had the same issue and the same fix for both 12.10 and 13.04.

---

### Post by mhzokaii on 2013-09-26
> **catsy said:**
> All right, I tried your fix. Thus far I've had no freezing. We will see how long this lasts...

Could you please let me know whether you have experienced any new freezes or not?
I had this problem since Ubuntu 12.04 and after going back again to CentOS, now I decided to use Debian 7.1.0, and guess, here I see exactly the same freezes!

---

