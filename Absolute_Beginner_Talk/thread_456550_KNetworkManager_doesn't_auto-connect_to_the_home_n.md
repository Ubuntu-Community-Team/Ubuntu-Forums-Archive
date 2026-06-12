---
title: "KNetworkManager doesn't auto-connect to the home network."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ZeroXR on 2007-05-27
I finished getting the last touches configured on my parent's Kubuntu machine, but I just have one last thing I need to figure out...

On boot-up, KNetworkManager starts up, but I can't find any option to make it connect automatically to my family's wi-fi router. I am a Ubuntu/Gnome user primarily, but I just can't figure out how to make it connect automatically to my network for the life of me. I have tried to Google for an answer and searched the forums to no avail.

Does anyone know how to make Kubuntu automatically connect to a home network automatically?

Thanks in advance!

---

### Post by Happy_Man on 2007-05-27
I believe (after a bit of hasty poking around) that if you set it so that you have the wireless network enabled (not wired) and set the KNetworkManager to autostart by right-clicking the icon--> Options --> Configure Autostart.... it will work. After all, if it works like that w/ a wired connection (eg mine), why not with wireless?

---

### Post by ZeroXR on 2007-05-27
**Happy_Man:** It is already set for Auto-Start, but the only thing is... It sees 3 networks total (2 being other  networks in the neighborhood), I just want it to connect directly to my family's router. On log-in/autostart, the machine is offline and you have to click KNetworkManager to see what networks are available to connect to. Is there a way to connect to the network without having to choose on auto-start or is there just no way to do that?

I know that Gnome's clients to connect to networks (Avahi or GTKwifi) automatically connect to a "preferred" network... I am just looking to make KNetworkManager do just the same.

---

### Post by Happy_Man on 2007-05-27
After some more poking around, I can't see anything that would do that. But then again, I can't properly test this, as I have a wired connection to a desktop (means no wireless). Sorry that I can't help more....

---

### Post by p_quarles on 2007-05-27
Have you searched the repositories for something like "kde wifi"? 

I used Kubuntu only briefly before going back to Gnome (more flexible, I think), but I'd guess there's something similar to the Sessions/Startup Programs options. It might be complicated, but that should allow you to run a terminal command to connect to a specific network on startup.

EDIT: I did that search, and only found the network manager that's packaged with kubuntu. Oh well.

---

### Post by ZeroXR on 2007-05-27
**p_quarles:** The machine is for my family... so I am trying to keep to things that have a GUI or an auto-starting mechanism. If it was my personal machine, I wouldn't mind. I just need to "idiot-proof" the machine.

---

### Post by p_quarles on 2007-05-27
ZeroXR --Yeah, I got that part, so maybe I wasn't very clear. In Gnome, you can configure automatic startup programs by going to Control Center/Sessions/Startup Programs. If you can figure out how to use a terminal command to link to the appropriate network, you might be able to add this to the startup sequence and get it to connect without any right-clicking or typing on the part of the user. Like I said, it might get complicated (for the person implementing it, not the user), but possibly worth attempting.

---

### Post by ZeroXR on 2007-05-27
**p_quarles:** No worries... It may have been a misunderstanding on my part. I know how to configure it on Gnome, but I just can't figure it on KDE for the life of me. I just turned on the system and KNetworkManager tried to connect automatically and failed, though on reconnection it linked up fine... So I am officially boggled...

Many thanks for the help though, the KDE Wifi packages are installed too, so hopefully that should help resolve things on the next reboot. It looks like my family is enjoying Kubuntu too much for me to try anything else tonight. :-)

---

### Post by Happy_Man on 2007-05-28
Have you tried installing GNOME's wireless manager? You know how to use it, and they do the same thing.... give it a shot.

---

### Post by ZeroXR on 2007-05-29
**Happy_Man:** I'll keep that in mind, even though I don't want to mix Gnome apps with KDE on their PC. Oddly, KNetwork manager automatically connects now and I can't figure out what happened. My family is definitely happy though, they love the machine to death!

---

### Post by Cimmo on 2007-10-27
Look at this
[http://launchpad.net/bugs/125767](http://launchpad.net/bugs/125767)

---

