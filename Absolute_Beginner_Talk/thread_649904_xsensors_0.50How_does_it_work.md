---
title: "xsensors 0.50:How does it work?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by sdim on 2007-12-25
Merry Christmas,everyone.

I've installed xsensors to take a look at my cpu and chassi fan temperatures,but I can't figure out how this program works.All I get is an empty card,when I click on the application.

Any answers are welcome.Thank you.

---

### Post by forestpixie on 2007-12-25
you need to first install lm-sensors

```
sudo apt-get install lm-sensors
```

then you need to run sensors detect

```
sudo sensors-detect
```

run through that - restart and xsensors should be working

---

### Post by sdim on 2007-12-26
Not working,but thanks anyway.

---

### Post by forestpixie on 2007-12-27
what's not working - post the errors

---

### Post by sdim on 2007-12-28
Application doesn't start at all.All I get is a window that is minimized and when I open it,there is nothing.

---

### Post by tgalati4 on 2007-12-28
Post the output of:

>sensors

You should get something like:

tgalati4@minty5:~$ sensors
w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.28 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.41 V  (min =  +5.86 V, max = +13.46 V) 
AVCC:      +3.30 V  (min =  +3.82 V, max =  +2.42 V) ALARM
3VCC:      +3.30 V  (min =  +3.57 V, max =  +3.44 V) ALARM
in4:       +1.61 V  (min =  +1.72 V, max =  +0.56 V) ALARM
in5:       +1.88 V  (min =  +2.04 V, max =  +1.85 V) ALARM
in6:       +5.17 V  (min =  +6.53 V, max =  +5.30 V) ALARM
VSB:       +3.25 V  (min =  +2.03 V, max =  +2.00 V) ALARM
VBAT:      +3.22 V  (min =  +3.82 V, max =  +2.77 V) ALARM
in9:       +1.61 V  (min =  +2.04 V, max =  +1.88 V) ALARM
Case Fan:    0 RPM  (min =  811 RPM, div = 128) ALARM
CPU Fan:   981 RPM  (min =  664 RPM, div = 8)
Aux Fan:     0 RPM  (min =  703 RPM, div = 128) ALARM
fan4:        0 RPM  (min =  811 RPM, div = 128) ALARM
fan5:        0 RPM  (min =  811 RPM, div = 128) ALARM
Sys Temp:    +39°C  (high =  +127°C, hyst =   -75°C)  
CPU Temp:  +44.0°C  (high = +70.0°C, hyst = +68.0°C)  
AUX Temp:  +49.0°C  (high = +80.0°C, hyst = +75.0°C) 

xsensors doesn't work for me either.  It can't handle the winbond 83627 chip.  I use xfce and I have the "sensors plugin" on the panel to display temperatures.

If lm-sensors doesn't work then you won't have any data to display.

---

### Post by Panhead Bill on 2007-12-31
Same results for me, > sensors has the data, but xsensors errors out with:

sensor "asb100" not supported by xsensors
sensor "w831785ts" not supported by xsensors

---

### Post by forestpixie on 2007-12-31
emm.. not sure then tbh - I don't get a problem - do you get sensible readings if you do sensors from terminal once it's set up

Edit - sorry half read your post - time for bed

---

### Post by Pethegreat on 2007-12-31
This is related to sdim's problem. I am looking for a CPU temperature monitor for the gnome desktop. I have been unable to find one. I did follow the instructions to install xsensors, but I have the same problem. It is probably due to the fact that I used a budget motherboard. Do you have any programs that will work?

---

