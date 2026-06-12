---
title: "Need to save this configuration!"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-11-19
I am supposed to shut down my system to take it to school tonight, and I need to find out how to keep the configuration I have right now...

Every time I need to re-boot, I have to go through a HUGE process to get my wireless working again. I have to uninstall ndiswrapper and the utils, remove it from /etc/network etc.etc. Then I have to go through the whole install thing again (ndiswrapper).

Does anyone know how I can make the setup I have RIGHT NOW permanent?

EDIT: I am using Breezy. It is the only release that works on my system.

Thanks!

---

### Post by jordanmthomas on 2006-11-19
Does hibernate work on your system?
If so, that would be the easiest (and only way I would know) to keep everything working well.

---

### Post by Papa-san on 2006-11-19
No... Actually it does, but my battery life is very short, and the trip is an hour and a half... Does hibernate keep settings after the batt dies? I don't know how it all works...

---

### Post by jordanmthomas on 2006-11-19
Hibernate does not use any battery power whatsoever.  It saves what's in your RAM onto disk and then when you power back up, it's all put back just like it was.

Suspend uses very little power, and you should be able to make it an hour and a half even with bad battery life (My laptop will run on suspend for well over a day).  Suspend turns off everything but your RAM, so it starts back up instantaneously with everything the way it was.

---

### Post by Papa-san on 2006-11-19
Well, I never got it set before I had to go, so I am re-setting everything... again.

I will try the hibernate settings when I need to go tomorrow night! I'll let you know what happens!

---

### Post by Papa-san on 2006-11-20
OK... Even after putting it in hibernation for the night, I had to change my network settings and activate my wireless. It didn't reactivate itself. Is there any way to make it boot with wireless active?

I also need to figure out how to be able to connect at school as well. in /etc/network/interfaces, my wlan0 only has the home essid and wep. At school, there isn't any wep key. The Essid is "FBBC Free1" But no matter what I do, it won't connect, even after I purge my home settings. I have to be doing something the wrong way...

---

### Post by Papa-san on 2006-11-21
I have it to where I only need to run my network GUI and 'activate' my wlan0. Then it comes up with my connection to my home router. However, if I re-boot, this 'active' status does not 'save'. I have to do it over again. 

Plus I still have no way to log in on my school's network.

---

### Post by yanqui on 2006-11-21
Even if hibernate could get it done, there's still the issue of the configuration settings not being saved.  any ideas on why that's happening?

---

### Post by stucky on 2006-11-30
I'm having similar issuse on my desktop. ndiswrapper has my wireless working just fine and I have my eth0 disabled. When I reboot, no connection. I have to got to System>Administration>Networking and then reset my location. After it runs through that, eth0 is reenabled but not configured. I have to disable it once more then go in to wlan0 and my WEP info is blank and reverted back to hexadecimal. After I enter the proper ASCII WEP key everything is back up and running. At least it's functional, so no griping there but it's a real annoyance to have to go through this after every reboot.

Any suggestions?](*,)

---

### Post by sunexplodes on 2006-11-30
after you get ndiswrapper setup have you done the 

ndiswrapper -m
modprobe ndiswrapper 

commands?

---

### Post by stucky on 2006-12-16
> **sunexplodes said:**
> after you get ndiswrapper setup have you done the 

ndiswrapper -m
modprobe ndiswrapper 

commands?

Yes, I've tried all of that. Strange thing is, now the only thing I can count on to keep we morking is NetGo which works great however I have to manually start it every reboot. I recently did a fresh reinstall and this problem has become even worse. Now instead of just disabling wlano and renabling eth0, it pooches my essid, wep and gatway IP entries. This is getting frustrating but thank God for NetGo. Anybody know how to get it to just fireoff at boot?](*,)

---

### Post by Papa-san on 2006-12-17
I ended up installing a new program called 'Connection Manager' located here:
[http://www.ubuntuforums.org/showthread.php?t=299462](http://www.ubuntuforums.org/showthread.php?t=299462)
I had very good luck with it, as have many others. There are, however, several people who have not!!!
Make a good backup before installing it!

Good luck!

---

