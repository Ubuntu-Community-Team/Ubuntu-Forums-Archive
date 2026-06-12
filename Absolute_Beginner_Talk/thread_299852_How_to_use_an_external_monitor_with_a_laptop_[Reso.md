---
title: "How to use an external monitor with a laptop? [Resolved]"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by az_s_za on 2006-11-14
Hi,

I have a Sony Vaio which is working well with Ubuntu 6.10.  The graphics card seemed to be recognised with the initial installation, but I am unable to use an external monitor which is plugged into the laptop's serial monitor port.

In WinXP I type Fn+F7 and can select external monitor, laptop monitor, or both at the same time.

I have seen other posts here where people have recommended Fn+F8 at startup or Fn+F4.  Neither of these work for me.

Incidently, other Fn+F# functions work fine, e.g. Fn+F5 dims the monitor.

How do I tell my system to send its signal to the external monitor?

Thanks.

---

### Post by hollaburoo on 2006-11-14
I know this is annoying and probably not a real solution but have tried booting up with the monitor plugged in?  That always gets my Nvidia to work...

---

### Post by robgill on 2006-11-14
I've asked and this is the best response I've gotten, but haven't been able to test yet.  It's to extend the desktop to two monitors.  Btw, I have a sony vaio fs640, so if you get to try, let me know.

[http://www.ubuntuforums.org/showthread.php?t=295369](http://www.ubuntuforums.org/showthread.php?t=295369)

[http://www.ubuntuforums.org/showthread.php?t=221174&highlight=Xinerama](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=Xinerama)

---

### Post by az_s_za on 2006-11-14
Thanks, I'll have a look at Xinerama if I don't get an easier solution, which should be possible as I don't need to run 2 monitors, I just want to run the whole desktop on one, external monitor.

No, booting with the external monitor attached doesn't work.

---

### Post by az_s_za on 2006-11-30
FYI, I have just find an answer that works perfectly for my purposes, here:
[https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVGN-TX3XP]("https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVGN-TX3XP")

which says, in part:
 > External monitor works?     Yes...
	
Have to edit xorg.conf (add Option "MonitorLayout" "CRT,LFP" and Option "Clone" "true" in device section) 

---

### Post by az_s_za on 2006-12-10
> edit xorg.conf:
In Device section, add: 
[I]Option "MonitorLayout" "CRT,LFP" 
Option "Clone" "true"[/I]

I have been using this for a week now, and there is only one problem... video, regardless of type, does not display on the external monitor.

Does anyone know how to get that working?

---

### Post by teitunge on 2007-01-21
**First**
sudo apt-get install i810switch

**Turn on CRT output**
i810switch crt on

and if you want to go back

**Turn off CRT output**
i810switch crt off



Hope it will help you out :)

---

