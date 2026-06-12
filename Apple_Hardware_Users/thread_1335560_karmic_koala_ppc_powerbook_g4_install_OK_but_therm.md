---
title: "karmic koala ppc powerbook g4 install OK but therm_adt746x fan issue"
date: 2009-11-23
forum: Apple Hardware Users
---

### Post by rednose0607 on 2009-11-23
Hi,

question for GURUs :) at end ...

just installed K.K. as per subject. For those with PB 15" PPC: I upgraded from 9.04 with troubles, better a fresh install. on cd prompt, press tab at yaboot prompt and type live-nosplash video=radeonfb:1280x854

verified as other posts here that b43 module (wifi) causes troubles on suspend/reboot. you need to unload it (rmmod b43) for a good suspend/resume

QUESTION:
after the fresh install the fan was working ok (!!!), therm* was just spinning the fan a bit. mac was quite. After a couple of boot, therm* is running the fan full throttle, and is not responsive to parameter passed on command line. The only way to have a quite mac is to disable the fan (comment out entry in /etc/modules). if later on you modprobe it with fan_speed=0 or whathever value, fan again full trottle, even if after you rmmod the module. Only way to have again a quite mac: reboot :(

ANY SUGGESTION????? THANKSSSSSSS :)

rednose

---

### Post by rednose0607 on 2009-11-24
Hi all,

little update: resuming after a suspend, there are troubles with the touchpad, it stops working. If you attach a mouse is ok.

On top of that, my last suspend/resume cycle ended up badly, need to power off. Basically the suspend/resume works ALMOST all the times ;-)

I ended up disabling the therm* module. After a day using the mac with therm* disabled, I heard the fan running "slowly". Probably it runs regardless of the sw when things getting "hot"

R.

---

### Post by dean.ryan on 2009-12-28
Hi there, does anyone know how to get the fan to turn on at all? I have an iBook G4 running Ubuntu 9.10 and Mac OS X. The fan works fine in OS X but not at all in ubuntu. Someone please tell me how to turn it on! It gets so hot i can't even touch it. PLEASE HELP!!!

Running iBook G4, 1.33 gHz PowerPC Processor, 512 MB Ram, OS X 10.5 and Ubuntu 9.10

---

