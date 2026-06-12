---
title: "Ati card temperature monitor?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by asdfqwert on 2008-03-22
After i restarted out of ubuntu and went to windows, i saw that the GPU temp was 70 C(wasn't doing anything intensive on ubuntu) when the normal idle temp is 50 C on my RADEON X800XL.

I had compiz effects turned on, but is there a temperature monitor/fan speed modifier for ati cards i can download for ubuntu?

---

### Post by Darganot on 2008-03-22
Open a terminal and run:

> sudo apt-get install lm-sensors

You should have a monitor to put in your panel.  on KDE:

> sudo apt-get install ksensors

---

### Post by asdfqwert on 2008-03-22
Can i change my GPU fan speed with it?

---

### Post by asdfqwert on 2008-03-22
Well actually, i've read that 70C while gaming(or while it's doing something intensive) is normal, the thing is that it said it was 70C, but before booting into windows, i wasn't even doing anything intensive on ubuntu.


And, i use Atitool to increase the fan speed, and it works.

---

### Post by asdfqwert on 2008-03-23
Ok, i installed it and ran 'sensors' in the terminal and got 

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +35°C



Don't see anything about my gfx card.

---

### Post by XaTriX on 2008-04-04
> **asdfqwert said:**
> Well actually, i've read that 70C while gaming(or while it's doing something intensive) is normal, the thing is that it said it was 70C, but before booting into windows, i wasn't even doing anything intensive on ubuntu.


And, i use Atitool to increase the fan speed, and it works.

How did you that ?

I want to reduce fan speed of my ATI card, but i don't find an utility which can offer that to me..
I've already tested Ati tool on linux with emulation (wine), but it did'nt work..

XaT

---

