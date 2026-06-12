---
title: "Hard drive errors in MacBook dual boot"
date: 2009-03-13
forum: Apple Hardware Users
---

### Post by ruru on 2009-03-13
I am dual-booting my 3rd Gen Macbook (white 2.2GHz model) with Leopard and Hardy and using rEFIt (there is also a 3rd FAT32 partition for shared storage). A while back, there was an Apple update which killed my laptop - it just never woke up after the post install reboot. I have reconfigured and reinstalled both systems many times since and even took the laptop back under warranty to be repaired (= knee-jerk replacement of logic board which changed nothing).
I now install OSX (which tells me the SMART status of my drive is 'failing', but otherwise runs fine)...until I do an update. I always end with an unbootable system after the update. I now use the machine without updates - but as time goes on, this becomes not so good. 
Ubuntu (my main OS), meanwhile, runs fine on the other partition and has never complained about failing discs.

Because I think the original update in question included an EFI update, I am wondering if it is possible that I have screwed something deep and meaningful by playing with rEFIt? Or is my hard drive just broke? (If so why didn't the Apple techs replace that instead of the logic board?) 

Does anyone out there have an idea what could be wrong? What other helpful info could I provide? There's stuff I'd like to install that requires a newer OS version...

---

### Post by cyberdork33 on 2009-03-13
refit cannot break your firmware. It doesn't touch it. It is a special kind of app that is launched by the Mac firmware. that is it.

If the SMART status of the drive is that it is failing, it is very likely that it is... especially since the logic board was just replaced.

Otherwise I have no idea why the update is giving you a problem. Do you have any third party upgrades? RAM? Hard Drive? etc?

---

### Post by ruru on 2009-03-14
I had added extra RAM shortly before the original problem occurred, but had used OSX with the new RAM OK - the first sign of a problem was that OSX never woke from that update. 

The OSX install is pretty clean - I hardly ever use it so not much is installed. Only rEFIt and Firefox above the basic Leopard stuff.

OSX was having trouble booting last night - it really looks like a dead drive. But I am confused why a) the Apple support rejected my suggestion that it was a hard drive problem and b) Ubuntu continues to work fine. Is there a way from Ubuntu to check the physical state of the drive?

---

### Post by cyberdork33 on 2009-03-15
> **ruru said:**
> I had added extra RAM shortly before the original problem occurred, but had used OSX with the new RAM OK - the first sign of a problem was that OSX never woke from that update. 

The OSX install is pretty clean - I hardly ever use it so not much is installed. Only rEFIt and Firefox above the basic Leopard stuff.

OSX was having trouble booting last night - it really looks like a dead drive. But I am confused why a) the Apple support rejected my suggestion that it was a hard drive problem and b) Ubuntu continues to work fine. Is there a way from Ubuntu to check the physical state of the drive?
there is some software called badblocks which can look for hard drive issues.

Ubuntu would work fine if none of the bad sectors are in the Ubuntu partition(s).

You might want to try reverting your RAM to the original stuff just to see if that has an effect. The Mac can be particular about what RAM you use in it.

---

### Post by ruru on 2009-03-20
I have installed and run GSmartControl [http://gsmartcontrol.berlios.de/home/index.php/en/Home]("http://gsmartcontrol.berlios.de/home/index.php/en/Home") which also indicated that the drive is failing - it seems that Ubuntu is just less sensitive to this than OSX (?) or maybe it's sitting on a cleaner part of the disc.

I will try badblocks on the laptop this evening as well...

I have tried removing RAM, but this doesn't have an effect. It looks like I simply need to order a new drive.

---

### Post by cyberdork33 on 2009-03-20
> **ruru said:**
> maybe it's sitting on a cleaner part of the disc.
that'd be my guess.

Looks like a new hard drive is in order.

---

