---
title: "Batt Life: It Sucks!"
date: 2009-09-04
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2009-09-04
Power usage is absolutely horrible in (K)Ubuntu. OS X I get about 3 hours on my battery, no compromises like turning things like desktop effects off either. In Ubuntu on the same machine I get a little over an hour. That's absurd...

I've tried using powertop, my cpu is set to ondemand.. non of this really makes a difference. I have also done things like disable bluetooth something I don't have to do in OSX. Battery life still sucks.

I don't think this is just macs either. Anyway what can we do about this? I mean it's a big deal especially with laptops now coming with 7 hour batteries.

---

### Post by Tompalaz on 2009-09-05
Can confirm this issue.
Have you tried to lower the screen brightness? In OSX it gives me ~30min+
However in Ubuntu I cant change the brightness, don't know why.:(

---

### Post by hanzomon4 on 2009-09-05
Yeah I can change it but it doesn't really help

---

### Post by Richardcavell on 2009-09-05
I also confirm this issue on my MacBook.

There's a theory that it has to do with the fact that even after installing Mactel packages, Ubuntu has no ability to modify the voltage going to the CPU, which is an SMC feature.  OS X can put the CPU into a lower power mode; Ubuntu can't.

Richard

---

### Post by tgalati4 on 2009-09-06
I think there are some serious power savings in the GPU that linux can't touch yet.  On windows xp, my GPU runs at least 5C cooler on "power saving mode" than in Jaunty.  I have an ATI FireGL3200 which can ignite kindling.

Even with dynamic clock turned on and declocking, there is still a thermal difference.

On a thinkpad t43p I get 2:10 on an older 6-cell battery (160 cycles, 46.9 Wh out of 53).  In winXP doing the same browsing tasks (ubuntu forums in firefox) I get 3:30.  The average power difference is ~19 watts in Ubuntu and 16 watts in winXP.  Those watts are going somewhere.

I have done all of the powertop tweaks, bluetooth off, etc.  It's a mystery.  I notice that 1/2 of my wakeups are from the acpi so perhaps there is some low-level stuff that needs to be looked at.

Edit:  I have not tried undervolting.  Perhaps the Windows XP ATI driver performs some undervolting besides declocking to achieve the 2-3 watts savings?  Anyone know?

---

