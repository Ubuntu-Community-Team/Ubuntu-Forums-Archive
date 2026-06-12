---
title: "Ubuntu on Mac Book Pro Retina Display is hot all the time"
date: 2013-08-09
forum: Apple Hardware Users
---

### Post by didi32 on 2013-08-09
I recently installed (dual-booted with refind) Ubuntu 13.04 64-bit on a MacBook Pro 15 with Retina Display. Everything seems to work well, however I've noticed that the computer is generally 20 celsius degrees hotter than on Mac OS X. I was wondering if anyone knows why that is, if there is a way around it, and finally if it is harmful at all and something to deal with. Here is the detail I get when I run sensors (lm-sensors) with only Emacs and Firefox opened:

sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +72.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +67.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +71.0°C  (high = +87.0°C, crit = +105.0°C)
Core 2:         +71.0°C  (high = +87.0°C, crit = +105.0°C)
Core 3:         +66.0°C  (high = +87.0°C, crit = +105.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Left side  : 2157 RPM  (min = 2160 RPM, max = 5940 RPM)
Right side : 1999 RPM  (min = 2000 RPM, max = 5499 RPM)
TB0T:         +37.8°C  
TB1T:         +37.8°C  
TB2T:         +36.0°C  
TC0E:         +72.2°C  
TC0F:         +73.8°C  
TC0P:         +54.2°C  
TC1C:         +69.0°C  
TC2C:         +70.0°C  
TC3C:         +71.0°C  
TC4C:         +69.0°C  
TCGC:         +70.0°C  
TCSA:         +70.0°C  
TCTD:          +0.0°C  
TCXC:         +71.2°C  
TG0D:         +61.8°C  
TG0P:         +58.5°C  
TG1D:         +67.0°C  
TG1F:         +66.8°C  
TG1d:         +61.0°C  
TH0A:         +64.0°C  
TH0B:         +64.0°C  
TH0V:         +46.8°C  
TH0a:         +64.0°C  
TH0b:         +64.0°C  

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +61.0°C  (high = +95.0°C, crit = +105.0°C)

Thank you,

---

### Post by didi32 on 2013-08-09
After installing macfanctld it does look like the fans are used in a better way. They start spinning harder a little earlier than when the package is not install. I'll use it for a little while longer and see if that helps.

---

### Post by r3dbeard on 2013-08-09
Various other suggestions include keeping your keyboard lights off unless needed, reducing screen brightness to <=90%, getting a cooling pad to increase air circulation, and using Safari vs any other web browser as it uses less resources. 

source links:
[http://apple.stackexchange.com/questions/17402/how-to-keep-your-macbook-pro-cool-unibody](http://apple.stackexchange.com/questions/17402/how-to-keep-your-macbook-pro-cool-unibody)
[https://discussions.apple.com/thread/4218055?start=0&tstart=0](https://discussions.apple.com/thread/4218055?start=0&tstart=0)
[http://askubuntu.com/questions/154098/is-unity-causing-my-macbook-to-run-near-burning-hot](http://askubuntu.com/questions/154098/is-unity-causing-my-macbook-to-run-near-burning-hot)

---

### Post by SilverOne on 2013-08-11
if i had to guess i'd say you installed ubuntu using the mac os version which in turn does not use efi boot and only gives you the nvidia card.

---

