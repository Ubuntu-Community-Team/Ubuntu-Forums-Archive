---
title: "Where are Kernel Panic messages logged ?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by vikram on 2007-04-10
I am using Kubuntu 6.10 and had to hard boot as the computer wasn't responding to any keys.

When I tried booting again I got a Kernel panic message and could only boot up in the safe mode. Where do I find that message ?

I tried /var/log/messages , syslogs but couldnt find it. Would like to know where to find these messsages before i can even start troubleshooting.

as a side effect I dont see any messages, splash screen on start up just a blank sceen till KDE comes up. any help here would be great.

thanks !

---

### Post by LaurelLynn on 2007-04-10
Dear vikram,

Try kern.log, or debug.  They both have kernal messages in them.

I´ve been wondering myself if there is a specific boot log. Once apon a time logs used to be spread out all over in Unix. But, poking around Ubuntu /var/log is the only place I have found system logs. So the message is probably in a log here.

---

### Post by vikram on 2007-04-10
thanks for your quick response Laurel  ! 

I'll search them when I get back home.

Any idea why I get a blank screen during the boot process ? It was working fine untill this error - i saw the Kubuntu logo and series of boot messages but now all I get is a blank screen untill KDE loads.

---

