---
title: "[SOLVED] Increasing (and installing) RAM"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-03-22
I recently had some good advice given in a thread concerning installation of RAM (thanks hyper_ch!).  However, I would be remiss if I did not check the advice was correct - there were limited posts - as I don't want to damage my work-horse (ie laptop).  I have 512MB DDR PC 333 RAM and want to increase it to 1024 MB.  The manufacturer suggested that I need to be careful about incompatibility, but others have suggested this is nonsense.  I wonder if this was a so-called financial consideration (Fujitsu wanted 94 quid, online it's about 20!) so...

1. Can I buy **_*ANY*_** 512MB DDR PC 333 RAM to go with the one I already have?

2. Is it just a simple case of opening the back, discharging the static and pushing it into the slot?

3. Do I need to configure anything, or will it just simply work?

4. Is there a command line I can input that will show what my computer hardware configuration is?

Many thanks in advance for the anticipated assistance (apologies to anyone "put out" by me checking their advice).  Regards.

---

### Post by StOoZ on 2008-03-22
yes it will be detected automatically.
regarding the command:
> lshw
will show everything

---

### Post by Bruce H. McCosar on 2008-03-22
> **Berean said:**
> 
1. Can I buy **_*ANY*_** 512MB DDR PC 333 RAM to go with the one I already have?

2. Is it just a simple case of opening the back, discharging the static and pushing it into the slot?

3. Do I need to configure anything, or will it just simply work?

4. Is there a command line I can input that will show what my computer hardware configuration is?


1:

Most of the time.  But to be safe, buy from a reputable place that offers a full refund in case of unexpected incompatability.

2:

Most of the time.  You must also clean out all the accumulated dust and make sure the area is actually ready to receive a card -- get cables out of the way and so on.  There are two little pins on either side of the card that lock into place and hold the card upright.  It may take you a bit to get this exactly right.  Study the other memory cards you already have installed on the board to see how its supposed to look.  Think "toaster with a very narrow pair of jaws attached at opposite ends."

3:

Most of the time it will simply work.  However, hardware manufacturers delight in surprises about as much as Santa Claus.  Just ask back if there's a problem; someone else out there might have run into the same peculiarity.

4:

lshw

(I believe it's installed by the package of the same name.)

---

### Post by Bruce H. McCosar on 2008-03-22
And in case you need a recommendation, I used Memory Ten:

[http://www.memoryx.net/](http://www.memoryx.net/)

---

### Post by jan quark on 2008-03-22
and run the command lshw and superuser to display every piece of information

```
sudo lshw
```

---

### Post by Berean on 2008-03-22
Sorry to start another thread (see [http://ubuntuforums.org/showthread.php?t=732168](http://ubuntuforums.org/showthread.php?t=732168)) but after lshw I find what I think is a potential problem! The following is copy/paste of part of the readout.

-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MB
             width: 64 bits

I was told by the manufacturer that I had 512mb RAM DDR PC 333 but the above would suggest that I have 2x256mb SDRAM and as I believe I only have 2 slots, wonder if I have any room for a RAM upgrade to 1024mb, other than replacing both 256mb.  Can anyone advise please?  Regards.

---

### Post by ugm6hr on 2008-03-22
best way to be certain is to get your laptop manual, open the RAM memory lid (which is often easily accessible) and just physically look at your RAM chips.

Most laptops only have 2 slots, so if you do have 2x256MB, then you can either buy a single 1GB stick and leave a 256MB in situ, or replace both.

Some memory apparently works faster if you use 2 identical chips though.

I find this quite useful for finding compatible memory: [http://www.orcalogic.co.uk/asp/memoryfinder.asp?ft=m&st=1](http://www.orcalogic.co.uk/asp/memoryfinder.asp?ft=m&st=1)

---

### Post by keeler1 on 2008-03-22
You need to make sure that the latencies are the same.  Most web sites that sell memory will tell you the cas latency and the timings.  You might want to try and figure out the latency and timings of what you have (your system bios might tell you) 

It is not that big of a deal though. If your second stick has faster timings than the first stick you should be fine from the start.  Your system might (this depends on how the manufacturer coded the bios) simply "underclock" the new stick to perform with the same timings as the old one.  However if the new sticks timings are slower most likely the system will be unbootable. 

I had that problem.  My new stick was slower and the system would power on and then fail.  To solve that, I had to manually configure the timings and latency in the bios setup.  However this was on my desktop.

Laptop bios normally are more minimal.  This means that you may not be able to configure the timings and latency and thus it is extremely important to get compatible memory.

I am not sure what kind of laptop you have but I know that dell sells memory upgrades for their laptops.  Other manufacturers probably do this as well.  While their prices will probably be more expensive they should at least give you the specs (the latency and timings) you need to go to another merchant and get memory that should be compatible.

---

