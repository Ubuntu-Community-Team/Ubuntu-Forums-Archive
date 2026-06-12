---
title: "Ubuntu 10.10: iMac 27&quot; i7: BE CAREFUL! There is an IMPORTANT Temperature issue!"
date: 2010-12-07
forum: Apple Hardware Users
---

### Post by jisaac on 2010-12-07
Hi,

Yesterday night Ubuntu was literally burning my iMac. It should be related to:
[http://ubuntuforums.org/showthread.php?t=1639269](http://ubuntuforums.org/showthread.php?t=1639269)

I'm trying right now the Fan control update from Mactel PPA:
[http://ubuntuforums.org/showpost.php?p=9793400&postcount=42](http://ubuntuforums.org/showpost.php?p=9793400&postcount=42)

This is what I'm experiencing now:
- "kacpid" uses 0% of CPU. Better.
- "macfanctld" around 4% of one Core.
- The iMac make more noise than during OSX sesions, because of new Fans speed.
- The temperature maintains to a more reasonable level but still hotter than during OSX sesions.

Let you know more as soon as possible.

---

### Post by jisaac on 2010-12-08
I've uninstalled "macfanctld" because "kacpid" comes back randomly using 90% of one Core (really don't know why).

Could someone using Ubuntu 10.10 and an iMac 27" i7 run "sudo hddtemp /dev/sda" and "sensors" in a terminal?

This is what I get after 2-3 hours of use (only consulting Internet):

> sudo hddtemp /dev/sda
/dev/sda: ST31000528ASQ: 42°C

> sensors
applesmc-isa-0300
Adapter: ISA adapter
ODD :        998 RPM  (min = 1000 RPM)
HDD :       1099 RPM  (min = 1100 RPM)
CPU :        939 RPM  (min =  940 RPM)
TC0D:       +129.0°C                                    
TA0P:        +19.0°C                                    
ERROR: Can't get value of subfeature temp3_input: I/O error
TG0P:         +0.0°C                                    
TG0D:        +49.2°C                                    
TG0H:        +48.8°C                                    
ERROR: Can't get value of subfeature temp6_input: I/O error
TH0P:         +0.0°C                                    
Tm0P:        +41.5°C                                    
TO0P:        +40.0°C                                    
ERROR: Can't get value of subfeature temp9_input: I/O error
Tp0C:         +0.0°C

PS: Don't like these errors...

---

### Post by alexmurray on 2010-12-08
The errors are normal since the driver doesn't always get a response from the hardware so in that case it returns an error. The real problem is kacpid taking like almost 100% of your CPU which means the CPU is always busy, generating lots of heat and hence heating up your machine - it really shouldn't be doing this - so instead of trying to increase the fan speeds to cool it down, I'd suggest trying to debug it from hogging the CPU so much. Looks like you're not the only one having this problem and that its not specific to your Macbook model either: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495694)

Also just noticed your comment on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577702) so I'd try the fix there mentioned and see if it does anything:

```
echo disable | sudo tee /sys/firmware/acpi/interrupts/gpe01
```

---

### Post by jisaac on 2010-12-09
Thanks alexmurray but I was already subscribed to this Bug (#577702) and no way, if kacpid appears, the workaround "echo disable | sudo tee /sys/firmware/acpi/interrupts/gpe01" does not work for me.

PS: I have an iMac, not a Macbook.

---

