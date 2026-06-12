---
title: "Ubuntu 12.04 PowerBook G4 heating"
date: 2014-10-31
forum: Apple Hardware Users
---

### Post by rican-linux on 2014-10-31
I have noticed that my PowerBook G4 has been running hot since installing Linux. The limit for the cpu sensor is 50 and actual tempature is showing 56 at times. Anyone run into this type of issue before?

linuxppc-laptop:~$ cat /sys/devices/temperatures/sensor1_limit 
50
linuxppc-laptop:~$ cat /sys/devices/temperatures/sensor1_location 
CPU BOTTOMSIDE
linuxppc-laptop:~$ cat /sys/devices/temperatures/sensor1_temperature 
60

---

### Post by este.el.paz on 2014-11-01
> **rican-linux said:**
> I have noticed that my PowerBook G4 has been running hot since installing Linux. The limit for the cpu sensor is 50 and actual tempature is showing 56 at times. Anyone run into this type of issue before?

linuxppc-laptop:~$ cat /sys/devices/temperatures/sensor1_limit 
50
linuxppc-laptop:~$ cat /sys/devices/temperatures/sensor1_location 
CPU BOTTOMSIDE
linuxppc-laptop:~$ cat /sys/devices/temperatures/sensor1_temperature 
60

[http://ubuntuforums.org/showthread.php?t=2221785](http://ubuntuforums.org/showthread.php?t=2221785)


In post #6 of that thread (which is for Intel issues) I mention the PowerPCFAQ which has some stuff on ways to tweak the therm_xx module.  So start with looking at the FAQ, the solution may be there. There should be a number of threads on getting 12.04 set up . . .??? 

 I've got 14.04 Lu going on my G4 iBook . . . fan is blowing due to having to concentrate on typing out this post . . . .

e.e.p.

---

### Post by rican-linux on 2014-11-01
This helped me my heating and fan issues.

[https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F)

Also a good place to check out as well for Linux on PPC is here:

[http://ppcluddite.blogspot.com](http://ppcluddite.blogspot.com)

---

### Post by este.el.paz on 2014-11-03
@rican-linux:

Thanks for posting back . . . looks interesting, might even help out on my iBook G4, fan seems to blow quite a bit with 14.04 Lu installed . . . .

e.e.p.

---

### Post by Kale_Freemon on 2014-11-06
Also, keep in mind that you are trying to run a more modern OS on a less than modern machine. That, in and of itself, could play a role in the heat generation.

---

### Post by reinhard-boris on 2014-11-10
There were quite a few changes to the whole cooling/ fan management internal stuff, of course you can only take advantage of that really if you use a more recent release, no problem with 14.04 and upwards on my iBook G4, on older distros you have to deal with this manually or might even run into issues that erroneously turn off the fans completly, which obviously is not good. :-({|=

In some of Apples products they used very high limits so fans would kick in rather late on OSX on quite a few systems (eg. iBooks), only rarely Apple adjusted these (later G5 desktop Systems did get an updated firmware for example to adjust a case of these but aside from those they pretty much had gotten away with it) you might argue too late which on the upside resulted in less noise but often reduced product lifetime, they had no shame really. I dual boot with Lubuntu and on the OSX leopard side of things I use "G4FanControl" to prevent early death.

---

### Post by rican-linux on 2014-11-10
I have heard that upgrading to 14.04 may break my sound. Have you had any issues with that?

---

### Post by reinhard-boris on 2014-11-10
Oh boy do I, how funny that you should ask :p I actually had looked into this the last few weeks, it is true but not far off from a solution but we still need some help!

You can help to make it work again in the future! Please read this: [https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr](https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr) (as I updated the wiki page a bit on cause and effect) and also this: [https://lists.launchpad.net/lubuntu-qa/msg04763.html](https://lists.launchpad.net/lubuntu-qa/msg04763.html) 

thx in advance
boris

---

### Post by rican-linux on 2014-11-10
How can I help? Upgrading to 14.04?

---

### Post by reinhard-boris on 2014-11-10
Hey, you can help from within (12.04)! :p

Just read these instructions and post your results (audio device id) in the same topic over here:
[http://ubuntuforums.org/showthread.php?t=2209340&p=12949568#post12949568](http://ubuntuforums.org/showthread.php?t=2209340&p=12949568#post12949568)

---

