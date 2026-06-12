---
title: "Can I install AMD graphic drivers with kernel 3.13 to turn off AMD GPU?"
date: 2014-05-22
forum: Any Other OS
---

### Post by kkantnaik on 2014-05-22
I installed LTS (Trusty) kernel in Elementary OS Luna and everything is working fine, infact I have seen some significant improvements in my system's performance. My laptop is less overheating and temperature stays around 60 degree celsius during normal usage and browsing.

The point is when I issue a sensors command
```
khirod@kurosaki:~$ sensors
```

output ```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +56.0°C  

radeon-pci-0100
Adapter: PCI adapter
temp1:       -128.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +57.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +57.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +55.0°C  (high = +80.0°C, crit = +85.0°C)
```

The temperature of PCI adapter is -128 degrees. Is sensors showing the wrong output??
Can I install open source drivers and turn off the discrete GPU??

And yes the kernel is 
```
khirod@kurosaki:~$ uname -r
3.13.0-24-generic
```

---

### Post by buzzingrobot on 2014-05-23
> **kkantnaik said:**
> 
The temperature of PCI adapter is -128 degrees. Is sensors showing the wrong output??
Can I install open source drivers and turn off the discrete GPU??

And yes the kernel is 
```
khirod@kurosaki:~$ uname -r
3.13.0-24-generic
```

Don't know why you are seeing a negative temperature reading, but disabling the Radeon -- assuming the machine also has onboard Intel video -- is done in the BIOS, not by the driver.  Obviously, don't disable the Radeon if it is the only video unit in the machine.

---

