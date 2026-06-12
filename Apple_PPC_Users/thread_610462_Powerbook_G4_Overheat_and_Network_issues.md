---
title: "Powerbook G4 Overheat and Network issues"
date: 2007-11-12
forum: Apple PPC Users
---

### Post by jef396 on 2007-11-12
I'm installing Ubuntu 7.10 on a Powerbook G4 and I have the following problems:

1.  After a few minutes of using the OS the fans speed up and a few minutes later it shuts off.

I have read some threads about therm_adt746x and found it to be running by using:

```
lsmod | grep therm
```

2.  I have an internal wireless card and an ethernet card.  Neither one is detected.  Running ifconfig only displays the loopback device, while clicking on "Manual configuration..." displays "Wired connection," "Wireless connection" and "Modem connection."

Both of these problems do not occur while using the LiveCD.

:guitar:

---

### Post by fredix on 2007-11-12
hi, i too have a G4 powerbook just recently install 7.10.. I have also been worried about the fact that it sounds like my HD is going to explode? but it hasn yet so i guess it should be ok, i wouldn´t mind a fix though:/

as for the wireless some has posted an easy fix here:

[http://ubuntuforums.org/showthread.php?t=526901&highlight=powerbook+g4+wireless](http://ubuntuforums.org/showthread.php?t=526901&highlight=powerbook+g4+wireless)

I just ran the script and now wireless works perfect. however does not work with WPA only WEP:( but still works so that is good.../f

EDIT: 

i am getting slightly worried about the temparature.. no **** it constantly very hot underneth.. like maybe 60-70 degrees?? does anyone know if there is something wrong, or is this ok? thanks f.


EDIT2: 

Just to le you know i am back to OSX as ubuntu just overheated and turned off (which i do not think is good)

Ok i have foudn another thread that descibes what seems to be happening with the overheating.. 

[http://ubuntuforums.org/showthread.php?t=12388&highlight=overheat](http://ubuntuforums.org/showthread.php?t=12388&highlight=overheat)

I think the jist is that there is no support for cpufreq? so the cpu runs at full power even if it is not doing anything. which is bad and possibly damaging? there is also a link to a bug report:

[https://bugzilla.redhat.com/show_bug.cgi?id=132422](https://bugzilla.redhat.com/show_bug.cgi?id=132422)

But being fairly new at this ubuntu stuff i do not fully understand enough to give it a go.. The bug also seems to be specific about the processor, Apple PowerBook Titanium II 550MHz and 667MHz. whereas i have a 1.33?

If anyone can make sense of this it would be great. because from what i have just read i do not think it is safe to use ubuntu in this condition?? thanks../f

---

