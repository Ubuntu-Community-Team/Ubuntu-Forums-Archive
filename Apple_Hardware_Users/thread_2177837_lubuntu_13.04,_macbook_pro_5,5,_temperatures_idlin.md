---
title: "lubuntu 13.04, macbook pro 5,5, temperatures idling at 62 celsius and other issues"
date: 2013-09-30
forum: Apple Hardware Users
---

### Post by jo5 on 2013-09-30
I already had previously installed refit and refind, because my cd driver is busted so I had to make a USB flash drive install with the dd command trick.

I installed sensors

```
coretemp-isa-0000Adapter: ISA adapter
Core 0:       +62.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +63.0°C  (high = +105.0°C, crit = +105.0°C)


applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   2000 RPM  (min = 2000 RPM, max = 6200 RPM)
TB0T:         +35.8°C  
TB1T:         +35.8°C  
TB2T:         +33.5°C  
TB3T:         +38.8°C  
TC0D:         +65.5°C  
TC0P:         +59.0°C  
TN0D:         +66.0°C  
TN0P:         +56.0°C  
TTF0:          +0.0°C  
Th0H:          +0.0°C  
Th1H:         +59.2°C  
ThFH:         +59.0°C  
Ts0P:         +33.2°C  
Ts0S:         +44.8°C  


nouveau-pci-0200
Adapter: PCI adapter
temp1:        +69.0°C  (high = +95.0°C, crit = +95.0°C)



``` 

I tried the echo 3000 command thing to increase the minimum fan RPM, even with sudo it says I don't have the permissions !
 
I don't really know what to do, I searched a lot though... Is there a fix planned in the 13.10 release ? How can I check I'm using refit the right way ?

I also could not manage to have some decent way to disable the touchpad while typing, I'm using lubuntu (LXDE) so there is no ticking box for this setting.

Anyways, it seems everything has better support than 3 years ago, so congrats to the contributors anyways ! But it would be even better if I could see my mac drop 5 or 10 degrees at least or more.

---

### Post by Vakman on 2013-10-02
You may be interested in this: [https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)
Also, this person here says EFI mode helps: [http://askubuntu.com/questions/345321/my-ubuntu-macbook-pro-feels-warm-can-i-solve-this](http://askubuntu.com/questions/345321/my-ubuntu-macbook-pro-feels-warm-can-i-solve-this)
You can also try Jupiter: [http://itsfoss.com/install-jupiter-ubuntu-1304/](http://itsfoss.com/install-jupiter-ubuntu-1304/)
You can also try a newer kernel version, newer than the one Ubuntu uses by default.

---

### Post by jo5 on 2013-10-03
> [COLOR=#000000]Also, this person here says EFI mode helps: [/COLOR][http://askubuntu.com/questions/34532...n-i-solve-this]("http://askubuntu.com/questions/345321/my-ubuntu-macbook-pro-feels-warm-can-i-solve-this")


Does this really apply to macbooks ?

And how do you know I'm not using EFI mode ? How can I know I'm using EFI mode or not ?

---

