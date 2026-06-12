---
title: "usb powered fan"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by kamakura on 2007-07-04
I recently switched from PCLinuxOS 2007 to Kubuntu 7.04 on my laptop.  I have a fan that sits under the laptop to keep it cool.  It is powered from a usb port.  The fan worked in Windows and PCLOS, however I haven't had any luck getting it to work in Kubuntu.  Any ideas on how I can get power to it?

---

### Post by hartz on 2007-07-05
These "dumb" devices sometimes draw power from the USB bus without registering on the bus.  I don't know how to solve the problem, but the first thing I would try is to see whether it registers.  Enter this command in a terminal:

lsusb

Look at the output - does any of the displayed items look like it might be the fan???

---

### Post by jasonlfunk on 2007-07-05
Get a can of air and blow out the dust in your laptop. You would be amazed how much this can cool it down.

---

### Post by kamakura on 2007-07-05
> **hartz said:**
> These "dumb" devices sometimes draw power from the USB bus without registering on the bus.  I don't know how to solve the problem, but the first thing I would try is to see whether it registers.  Enter this command in a terminal:

lsusb

Look at the output - does any of the displayed items look like it might be the fan???

No, it doesn't appear that it detects anything is plugged in.

---

### Post by hartz on 2007-07-06
That is a pity.  I've done a (cursory) search on Google and cannot find anything similar.

Did you have any luck with jasonlfunk's suggestion?

Cheers!

---

### Post by kamakura on 2007-07-06
It's not so much an issue of how much it heats up (I really only notice after having it sit directly on my lap for long periods of time), as much as it is an issue of getting it working.

I'm not sure what has changed, but it is working now.  Just to verify that it wasn't a problem with the device, I connected it to my wife's windows computer.  My laptop was off when I disconnected it.  I connected it back to my laptop and booted up.  It immediately worked and I can't get it to fail now.  The output of lsusb has not changed, so I think I will just enjoy the fact that it is working and hope it continues to do so.

Thank you for your help.

---

### Post by Old Pink on 2007-07-06
[LIST=1]
[*]Plug it in
[*]Type **dmesg** in terminal
[*]Paste the last few lines of relevant output here. :)[/LIST]
Should help us work towards getting it working. :) 

Have you tried it in another computer? The fan may have broken and this be a pure coincidence. 

At least try another USB port. :)

---

