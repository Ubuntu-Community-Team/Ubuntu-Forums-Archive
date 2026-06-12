---
title: "is my gpu really this hot? GPU 2 Heatsink @ 128*C"
date: 2010-06-02
forum: Apple Hardware Users
---

### Post by miatawnt2b on 2010-06-02
```

coretemp-isa-0000
Adapter: ISA adapter
Core0:       +56.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core1:       +55.0°C  (high = +105.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Left Fan:                   2001 RPM  (min = 2000 RPM)
Right Fan:                  1997 RPM  (min = 2000 RPM)
TB0T Enclosure Bottom 0:     +36.0°C                                    
TB1T Enclosure Bottom 1:     +36.0°C                                    
TB2T Enclosure Bottom 2:     +31.2°C                                    
TB3T Enclosure Bottom 3:     +38.5°C                                    
TC0D CPU Diode:              +59.5°C                                    
TC0F CPU ???:                +53.8°C                                    
TC0P CPU Pin:                +54.2°C                                    
TG0D GPU Diode:              +63.0°C                                    
TG0F GPU ???:                +57.2°C                                    
TG0H GPU Heatsink:           +52.5°C                                    
TG0P GPU Pin:                +56.0°C                                    
TG0T GPU Transistor:         +58.2°C                                    
TG1H GPU 2 Heatsink:        +128.0°C                                    
TN0D Northbridge Diode:      +58.5°C                                    
TN0P Northbridge Pin:        +57.0°C                                    
TTF0 Unknown:                +49.0°C                                    
Th2H Heatsink 2:             +50.8°C                                    
Tm0P Memory Controller:      +48.2°C                                    
Ts0P PCI Express Slot Pin:   +33.8°C                                    
Ts0S PCI Express Slot (unk): +46.2°C                                    

millerjw@MacBookPro:~$ 

```

Running fresh lucid build on a MBP 5,2 as per the community docs.  does anyone else's sensors look like this?

---

### Post by cj.surrusco on 2010-06-02
I don't really think that the heat sink temperature matters for your graphics card that much as long as the core temp is only around 55 degrees, as in your case. I'm not sure how that high temperature would affect the other components of your laptop, though. I doubt that the temperature is really that hot anyway, there is probably a fried thermometer in there or something. 126 degrees is REALLY hot.

---

