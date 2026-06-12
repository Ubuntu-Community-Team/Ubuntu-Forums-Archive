---
title: "identify sensor TTF0?"
date: 2012-12-30
forum: Apple Hardware Users
---

### Post by cj123 on 2012-12-30
I haven't installed the applesmc module or macfantl. The fans turn on when the cpu heats up and they cool things down except for two sensors (TTF0 and TW0P) -- which typically run hot without kicking up the fan . I am not sure if this is a problem. Sometimes the laptop is a bit hot for comfort on my lap but that was the case with osx too. I've read that TW0P (wireless proximity) typically runs hot and apple is of the opinion that it isn't a problem (ha ha.) whether I take additional steps to keep the temperature under control depends for me on what TTF0 is. All I've done is set the cpu frequency governor to conservative -- I'm running mint xfce if it makes a difference. I couldn't find the identity of TTF0 after searching for some time. Anyone have any idea?

below is my readout. 

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +52.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +52.0°C  (high = +100.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   1795 RPM  (min = 1800 RPM)
TB0T:         +31.5°C  
TC0D:         +51.0°C  
TC0P:         +50.2°C  
TM0P:         +57.0°C  
TN0P:         +49.0°C  
TTF0:         +65.0°C  
TW0P:         +73.0°C  
Th0H:         +49.2°C  
Th0S:         +49.2°C  
Th1H:         +49.2°C

As you can see, minimum fan activity despite high temps for those two sensors. I have a macbook 3,1 and I think the sensors on this model are a little different than on other macbooks. What's curious is that it doesn't have the sensor for the gpu that I believe is used in macfctl. If I were to use some sort of fan control maybe I should configure it to monitor the motherboard (TM0P)?

Best!

---

