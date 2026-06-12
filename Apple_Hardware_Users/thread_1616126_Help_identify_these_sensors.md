---
title: "Help identify these sensors"
date: 2010-11-07
forum: Apple Hardware Users
---

### Post by blueridgedog on 2010-11-07
I want to build some temp monitoring into conky on my macbookpro. 

Can anyone tell me what the human names are for these?


```
applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  1999 RPM  (min = 2000 RPM)
TB0T:        +35.5°C                                    
TB1T:        +35.5°C                                    
TB2T:        +35.0°C                                    
TC0D:        +52.0°C                                    
TC0P:        +47.8°C                                    
TN0D:        +51.2°C                                    
TN0P:        +43.8°C                                    
TN0S:        +59.8°C                                    
TN1D:        +59.0°C                                    
TN1F:        +59.8°C                                    
TN1G:        +90.0°C                                    
TN1S:        +59.8°C                                    
Th1H:        +46.0°C                                    
Ts0P:        +34.5°C                                    
Ts0S:        +42.0°C  
```

---

### Post by alexmurray on 2010-11-07
See [here](http://mactel-linux.sourceforge.net/wiki/AppleSMC) for info on decoding the meaning of the sensor names.

---

### Post by blueridgedog on 2010-11-07
Based on that I have the following:

TB0T:        +35.5°C	Enclosure - Bottom                                  
TB1T:        +35.5°C	Enclosure                                
TB2T:        +35.0°C    Enclosure                       
TC0D:        +52.0°C	CPU Die                                  
TC0P:        +47.8°C	CPU Proximity                                    
TN0D:        +51.2°C	Northbridge Die                                    
TN0P:        +43.8°C	Northbridge Proximity                                    
TN0S:        +59.8°C                                    
TN1D:        +59.0°C                                    
TN1F:        +59.8°C                                    
TN1G:        +90.0°C	Graphics Chip (assuming based on temp)                               
TN1S:        +59.8°C                                    
Th1H:        +46.0°C	Heatsink                               
Ts0P:        +34.5°C                                    
Ts0S:        +42.0°C

Any ideas as to some of the others?

---

