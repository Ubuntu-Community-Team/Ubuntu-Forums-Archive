---
title: "Reading iMac temperatures"
date: 2012-09-11
forum: Apple Hardware Users
---

### Post by scognito on 2012-09-11
Hi,
I want to know the temperatures of the components of my iMac 21.5 2011.
Running "sensors" I get a bunch of codes that I can't associate with (for example) CPU/GPU/HD.
Are they mapped somewhere?
I'm guessing TG0D should be the GPU and if it is...I think it is too hot :P
Any guess? Here is the output of sensors:

# sensors
applesmc-isa-0300
Adapter: ISA adapter
ODD :        1146 RPM  (min = 1000 RPM)
HDD :        1099 RPM  (min = 1100 RPM)
CPU :        1200 RPM  (min = 1200 RPM)
TA0P:         +31.2°C  
TA0V:         +31.2°C  
TA0p:         +32.2°C  
TC0H:         +44.2°C  
TC0P:         +52.2°C  
TC0c:         +49.0°C  
TC0h:         +44.2°C  
TC0p:         +52.2°C  
TC1c:         +48.0°C  
TC2c:         +46.0°C  
TC3c:         +48.0°C  
TCGc:         +49.0°C  
TCSc:         +49.0°C  
TCXc:         +49.8°C  
TG0D:         +79.8°C  
TG0H:         +74.2°C  
TG0d:         +79.8°C  
TG0h:         +74.2°C  
TG0p:         +75.0°C  
TH0O:          +3.0°C  
TH0o:         +52.0°C  
TH1O:          +3.0°C  
TL0P:         +40.8°C  
TL0V:         +44.5°C  

Thanks in advance!

---

### Post by scognito on 2012-09-11
Ok sorry, I found the solution according to this URL: [http://www.parhelia.ch/blog/statics/k3_keys.html](http://www.parhelia.ch/blog/statics/k3_keys.html)

TA0P 	Ambient temp 

TC0D 	CPU 0 die temp
TC0H 	CPU 0 Heatsink temp
TC0P 	CPU 0 Proximity temp

TG0D 	GPU 0 die temp
TG0H 	GPU 0 Heatsink temp
TG0P 	GPU 0 Proximity temp

TH0P 	HardDisk proximity temp
TL0P 	LCD proximity temp
TO0P 	Optical Drive proximity temp 

So seems my CPU is on around 52°C, where GPU is 75°-79°C and HD is 52°C.
I guess the GPU is really hot why the rest is ok?

---

### Post by scognito on 2012-09-12
You can add this at the end of /etc/sensors3.conf
> 
chip "applesmc-isa-0300"

    label "temp1"  "Ambient"                  #TA0P
    label "temp7"  "CPU heatsink"             #TC0h
    label "temp8"  "CPU proximity"            #TC0p
    label "temp15" "GPU die"                  #TG0D
    label "temp16" "GPU heatsink"             #TG0H
    label "temp23" "Optical drive proximity"  #TL0P

So the output of sensors is more readable:
$ sensors
applesmc-isa-0300
Adapter: ISA adapter
ODD :                    1264 RPM  (min = 1000 RPM)
HDD :                    1550 RPM  (min = 1100 RPM)
CPU :                    1198 RPM  (min = 1200 RPM)
Ambient:                  +31.5°C  
TA0V:                     +31.2°C  
TA0p:                     +32.5°C  
TC0H:                     +46.5°C  
TC0P:                     +54.5°C  
TC0c:                     +52.0°C  
CPU heatsink:             +46.5°C  
CPU proximity:            +54.5°C  
TC1c:                     +52.0°C  
TC2c:                     +51.0°C  
TC3c:                     +51.0°C  
TCGc:                     +51.0°C  
TCSc:                     +52.0°C  
TCXc:                     +51.8°C  
GPU die:                  +80.5°C  
GPU heatsink:             +75.0°C  
TG0d:                     +80.5°C  
TG0h:                     +75.0°C  
TG0p:                     +76.0°C  
TH0O:                      +5.0°C  
TH0o:                     +44.0°C  
TH1O:                      +5.0°C  
Optical drive proximity:  +48.0°C  
TL0V:                     +49.5°C  

Hope it helps

---

