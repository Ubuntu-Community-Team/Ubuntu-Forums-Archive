---
title: "NVIDIA Graphics Driver breaks suspend?"
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by hyperboloid on 2009-04-08
Just installed the NVIDIA version 180 graphics driver and activated it - now suspend fails. Anyone else getting this?

To be more precise: suspend seems to work as usual, but upon resuming after suspend I get a blank screen with no keyboard, and have to reboot. Every time.

---

### Post by agorf on 2009-04-09
Same here.

---

### Post by hyperboloid on 2009-04-09
I have reverted to Version 177 of the driver, and once again suspend works perfectly. 

Anyone have any idea why Version 180 might break things? Or where I should look to see what might be amiss?

---

### Post by dogscoff on 2009-04-10
Same problem here. Card is a Nvidia GEForce 8600M GS (512 meg ram). OS is Vanilla Ubuntu Intrepid, with Compiz enabled. Suspend was fine with the old driver (177) but now it refuses to come back up, exactly as Hyper describes. I have to hold down the power button for 5 seconds to hard-reboot the machine.

Anyone know where to send bug reports? The driver is written and maintained by Nvidia themselves so...

---

### Post by dogscoff on 2009-04-10
Forgot to mention, I am running 64 bit.

---

### Post by Dirjel on 2009-04-10
Same here.  I'm switching back to the 177 driver, until someone who knows what they're doing explains why it doesn't work XD

I'm on a 32 bit machine, though.

---

### Post by jamesey on 2009-04-11
the 180 drivers gave me problems too on jaunty until recently. I think some recent jaunty updates have fixed them. 

I was getting freezes anytime I started a video of any filetype
I was getting freezes making my desktop cube rotate
I was getting freezes with animation effects turned on in compiz. 
It all seems to be fixed now

---

### Post by Dirjel on 2009-04-15
Um, I didn't realize this thread was for Apple computers when I searched it, but I imagine you guys can do the same thing I did.

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

I'm pretty sure I had to do that before to get suspend working properly, but I guess I had to re-do it for the new driver.  I'm now using 180, and suspend works fine again.  Yay.

---

### Post by tactus on 2009-04-17
Premature driver for sure.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/306315](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/306315)

Reverted to 177 version as suggested here, suspend to ram works as expected again, thanks.

---

