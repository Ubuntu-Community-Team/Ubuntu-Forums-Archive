---
title: "brightness control, overheating, battery duration in Powerbook 12"
date: 2006-08-29
forum: Apple PPC Users
---

### Post by a.panico on 2006-08-29
Hello

I've a Powerbook 12" 1'5Ghz (6,8\) with MacOs and Ubuntu.
I currently can't control brightness on my laptop. I have searched in thousands of forums and find various references to brightness problems but I'm very tired of this issue. I've tried everything: update to Edgy, change the /etc/pbbuttonsd.conf configuration; also i've used two kernels: 2.6.15-26 and 2.6.17-6. 

I've pbbuttonsd, gtkpbbuttons-common, gtkpbbuttons-gnome, pbbuttonsd-dev and powerprefs installed.
i tried to use the 'pbbcmd' command to change the brightness manually, but i had not response.

Finally, in one forum I read that the brightness works in Gentoo and... it's true!!!!!!!!!
But like I love Ubuntu, I tried resolved this issue using the /etc/pbbuttonsd.conf of Gentoo, but doesn't work. 
I have heard also that the brightness works in Debian Unstable, but i haven't tried.

So, Has somebody resolve this problem??????????????????

Another issue is the overheating. I think that power management of Ubuntu/PPC isn't very good yet. I've configured the module therm_adtxxx (with parameters limit_adjust, fan_control) and i've been monitoring the temperature with an applet. That one up very quickly with no too overload, only with a few programs. When I've tried compile the kernel, the processor temperature go to +65ºC and then it shutdown for avoid damage. 
The battery's duration is shorter than OsX. Ubuntu devour it quickly (2h.30min approx.; 4h.30 in OsX).

What's the problem??????? My configuration???????](*,) 

I'm sure that step by step the community will resolve this issues and GNU/Linux will be better than MacOs. Because the freedom don't have price.

Sorry for my english...
                         Thanks!                

=================================
Apple, Nvidia, Broadcom... f??k off!!!!!!!! :evil:

---

### Post by APU on 2006-08-30
I have exactly the same Powerbook.

Brightness control does not work for mee too but I had not yet time to try this out since I´m still trying to get some sort of hibernation (suspend to disk) to work and some other stuff. Interestingly the system is able to reduce brightness before the tft goes too sleep to save energy. Therefore I think this is a bug in pbbuttonsd and not in the Ubuntu kernel configuration. The pbbuttonsd version included in Dapper is 0.7.2, currently version 0.7.8 is already available - maybe an update would help.

Regarding the Overheating. I constantly measured the CPU temperature on this PowerBook when I still had MacOS X running (from 10.3.x to 10.4.7). It reached 65° C every time I had a CPU intense task running vor at least several minutes. Normally it the temperature topped out at about 69° C and I never had a problem with that! And 65° C is not really hot for a current CPU so there might be another problem involved. Maybe just the measurement is wrong  ?

APU

---

