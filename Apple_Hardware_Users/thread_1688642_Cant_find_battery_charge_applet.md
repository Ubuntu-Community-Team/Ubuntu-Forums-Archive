---
title: "Cant find battery charge applet?"
date: 2011-02-15
forum: Apple Hardware Users
---

### Post by mathew89 on 2011-02-15
So i just installed 10.04 LTS on my ibook G4 late 2004 model and it works great i partioned my Hd and have osx on 1 and ubuntu on the other and updated it last night and installed to drivers for wireless etc... but i dont see a way to monitor my battery status on the upper bar? when i try to add to panel there is no battery charge applet or whatever? when i enter this into the terminal   

" 
sudo add-apt-repository ppa:iaz/battery-status && sudo apt-get update
sudo apt-get install battery-status

Terminal then asks for my password but it wont let me type any sort of
password? not even my login password so i do not know what password
terminal wants when none of the keys work?

So how can i monitor my fricking battery status here ?

[FONT=monospace]
[/FONT]

---

### Post by linuxopjemac on 2011-02-16
modprobe pmu_battery

and add pmu_battery to /etc/modules

---

### Post by drpjkurian on 2011-02-16
Well
I SUGGEST YOU TO DOWNLOAD THE GNOME APPLETS
TRY THIS [LINK]("http://http://linux.softpedia.com/progDownload/Gnome-applets-Download-4633.html")

---

### Post by drpjkurian on 2011-02-16
Hi Mathew
Please also note that when you type sudo password. It does not get displayed in the screen for security reasons....

---

### Post by mathew89 on 2011-02-16
after doing some digging i found out about the sudo password and the terminal display gui thing... i also now have got the battery indicator to show and the battery options tab is now displayed in power manager but as soon as i added the pmu_battery to modules and then upgraded from 10.04 LTS to the current my sound doesnt seem right now? b4 it had the right hardware for sound and now it does not i can use the ibook keyboard to increase/ decrease volume but the sounds icon shows no changes at all anymore?

---

### Post by linuxopjemac on 2011-02-16
that has nothing to do with pmu_battery. It probably has to do with alsa?

---

### Post by mathew89 on 2011-02-16
i didnt say it had to do i was just stating that after i had finished doing all that and updated now that doesnt work??? what the fix or how can i diagnose, VERY new to linux but its growing on me!

---

### Post by linuxopjemac on 2011-02-17
Give me the output of:
```
cat /etc/modules
```
please

---

### Post by mathew89 on 2011-02-17
pmu_battery

---

### Post by mathew89 on 2011-02-17
here are a few shots of sound manager and my upper right status bar notice the battery icon works not but even at full volume the sound status icon shows no audio or whatever?

---

### Post by linuxopjemac on 2011-02-17
add```

snd-powermac
```
to /etc/modules
as well

---

### Post by mathew89 on 2011-02-17
command not found it said? here is a pic

---

### Post by linuxopjemac on 2011-02-18
```
sudo nano /etc/modules
```
add the following line (for example after pmu_battery):
```
snd-powermac
```
it will look like this then:
```
pmu_battery
snd-powermac
```
CTRL-X and "y" to save
reboot

---

### Post by mathew89 on 2011-02-18
still no sound?

---

### Post by linuxopjemac on 2011-02-19
maybe you have to unmute some channels with
```
alsamixer
```

---

### Post by mathew89 on 2011-02-19
i get no file or directory or whatever, and the thing is nothing is muted and all volume is max, when in sound manager it shows no hardware and same for output it says dummy output but before i updated and everything it was working in 10.04! i used to get the startup chime not i dont?

---

### Post by linuxopjemac on 2011-02-19
sorry mathew, I can't help you more with Ubuntu. Ubuntu gave up support for PPC long time ago. Maybe it's time to switch...

What you can try is:
```
sudo alsactl init
```

```
 cat /proc/asound/cards
 0 [Screamer       ]: PMac Screamer - PowerMac Screamer
                      PowerMac Screamer Rev 0
```

[http://wiki.debian.org/ALSA](http://wiki.debian.org/ALSA)

---

### Post by linuxopjemac on 2011-02-19
startup chime can't be controlled from within Linux. You probably muted last time you used OSX.

---

### Post by mathew89 on 2011-02-20
what i meant was not the osx startup chine the ubuntu startup tune or sound whatever you want to call it?

---

### Post by linuxopjemac on 2011-02-20
> what i meant was not the osx startup chine the ubuntu startup tune or sound whatever you want to call it?
No idea, but does it mean you have sound working now ?

---

