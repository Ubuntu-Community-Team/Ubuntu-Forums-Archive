---
title: "lm-sensor problem (eeepc 1101HA &amp; maverick meerkat)"
date: 2011-06-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by titoff on 2011-06-02
Hi everyone

I have been trying for the last few days to monitor the temperature of my computer with lm-sensors and sensors applet.
Here is what I get using the sensor command:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +80.0°C  (crit = +86.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +25.0°C  (crit = +90.0°C)

Notice the discrepancy between the two temperatures. The acpi temperature reading seems to freeze at 80°C after 15mn of web browsing. From the moment I turn on the computer to that point, the acpi temp stays within the 40-55°C range, then a second later it get to 80°c and the acpi temp reading freezes. However, the coretemp remains in the 25-40°c range even hours later, and does not freeze.

So, which is the right temperature?  I wonder if there is a problem with the sensors  or if i am simply overheating my computer ?

---

