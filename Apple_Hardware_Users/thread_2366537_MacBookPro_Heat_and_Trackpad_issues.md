---
title: "MacBookPro: Heat and Trackpad issues?"
date: 2017-07-18
forum: Apple Hardware Users
---

### Post by sterator on 2017-07-18
My first full day with a dual-boot, OS X + Ubuntu Mac Book Pro.



[LIST]
[*]A bit concerned that the MBPro gets warmer when booted into Linux than OS X - same activity level seems to produce more heat. Is this because Linux can't communicate with the hardware in a way that conserves energy?


[*]Trackpad behavior is...insane. Lots of clicks, scrolls moves and other commands that I  don't intend. Trackpad and Ubuntu appear to be squirrelly..operating according to...whatever. Is there a driver to help this which I can install?


[/LIST]



Thank you!

---

### Post by miqrojamie on 2017-07-20
MacOS is heavily optimised for the specific hardware it runs on. That probably explains why it produces less heat.

As for the trackpad problem, I had a similar issue a while ago with an Air 2015 11" with it randomly clicking whenever I would type, I think it may be a problem with the open-source driver provided for it. I haven't dabbled with the mouse options in Ubuntu, but if there's an option to change the sensitivity, that might help. Don't count on it, though.

---

### Post by BenginM on 2017-07-20
Salutations !

for the Trackpad mouse options and sensitivity , you may want to look at xinput & xset ..

for the heat , install and setup lm-sensor and use Psensor and there is also thermald  ...

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

is a tool developed by Intel's Open Source Technology Center which monitors and controls the CPU tem. Thermald tries to prevent the CPU from overheating without a significant impact on performance by using some specific Intel functions available in the Linux Kernel. According to the Ubuntu

[https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues](https://wiki.ubuntu.com/Kernel/PowerManagement/ThermalIssues)

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

