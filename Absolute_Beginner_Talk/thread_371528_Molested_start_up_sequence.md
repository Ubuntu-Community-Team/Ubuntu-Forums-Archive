---
title: "Molested start up sequence"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by .:. on 2007-02-27
For the last week or so I've been playing around with Dapper Ubuntu trying to get my wireless card working (wg311v3). I'd reinstalled the driver for the umptenth time and set about restarting the card.

sudo ifdown wlan0 <-- worked fine
sudo ifup wlan0 <-- the computer crashed

I waited ~5 minutes then turned off the computer at the wall. Since then I've been unable to get back into the OS. When the start up hits "Loading manual drivers..." the whole thing freezes up. I'm not sure if it's related but "Starting PCMCIA services..." fails - though it's always done that.

I'd be quite happy to wipe the OS and start again from scratch (I'm at the point of ripping out my hair and taking an axe to the computer over the wireless thing) but I've dumped some files on there I'd like to get off first.

Is there any way to get these files back? I tried using a (hoary I think) Live CD but was unable to access the hard drive. I thought I should ask for help before doing any more damage.

Thanks in advance for any help!

---

### Post by chuckyp on 2007-02-27
You should be able to boot to a live cd or in recovery mode with the nopcmcia option.  That will definately make sure the card won't load.  Then you can recover files as you wish.  You may also want to try getting your wifi card working on a live cd.  Then do an install once you have the steps ironed out.

Possibly take a look at edgy or fiesty they both have better networking support than dapper.

---

