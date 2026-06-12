---
title: "palm sync"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by lavikl on 2007-05-26
Hey everyone !
I'm using Sony Clie palm, with palm 4 OS running it.
I installed gnome-pilot and i can't seemd to sync it with Evolution.
no matter which configuration i'm using, every time it says it can't find the Palm.
I'm using the same devices in WinXP and it works fine there with Hot sync.

I hope someone got an idea

Lavik

---

### Post by mättu on 2007-05-26
try this & post if successful, please:

install using synaptic:
jpilot
pilot-link

fire up jpilot
set ->file->settings->settings: serial port to /dev/pilot (assuming your conncting with usb-cable)
plug in palm
press hotsync on palm first
wait 3 seconds
press hotsync in jpilot

this works for me, because I can do without evolution.

works?

have fun
:m)

---

### Post by lazyart on 2007-05-26
I second jpilot.  Works like a charm.

---

### Post by mättu on 2007-05-26
just because I'm curious:
does it make a difference which button you press first (craddle / jpilot) or if you omit the "3-s-delay"?

---

### Post by lazyart on 2007-05-26
For me it only works if I hit sync in jpilot first.  If I go to the palm first it sometimes opens up the evo sync tool.

---

### Post by lemmy999 on 2007-05-27
@mättu

Great how to. Worked like a dream

Thanks

---

### Post by lavikl on 2007-05-27
First of all thank you for the help.
when i start the sync i get the following warning :

> failed to connect using the device  'cardle', on port '/dev/ttyUSB0'. check your
configuration, as you requested old-style usbserial 'ttyUSB' syncing, but
do  not have the usbserial 'visor' kernel module loaded. You may 
need to select  a 'usb' device. 

I configures jpilot to use /dev/pilot and  Preferences -> palmOS device  to use USB and /dev/pilot as well.

and the log file  saying :

> PC ID is 0.
I generated a new PC ID.  It is 734137970
****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished


I hope one of you encountered and solved some problem simillar to this 
:sad:

---

### Post by lazyart on 2007-05-27
If you are using Feisty and are connected by usb, change the port to "usb:"-- it's super simple that way.

---

### Post by lavikl on 2007-05-27
I'm using Feisty so like you said I've changed the port to : 

usb:

in prefs -> PalmOS -> port
and in j-pilot  prefs as well.
 
this time i don't get any error warnings, it seems the palm and Feisty just can't find each other 
Maybe i got it all wrong, can you please explain a bit further ?

---

### Post by lazyart on 2007-05-27
did you try install user from jpilot?

If you're not using evo to sync then do worry about the PalmOS settings.  Infact I purposely set my PalmOS settings incorrectly so it doesn't interfere.

---

### Post by lavikl on 2007-05-27
I installed a user in J-pilot, 
still it can't find the palm device.
the log file says :

> J-Pilot: sync PID = 8882
J-Pilot: press the hotsync button on the cradle or "kill 8882"
 and there's no warning or anything

---

### Post by Shawn Reist on 2007-12-17
Hello,

I have Ubuntu 7.10 installed and I have a Palm TX.

I set up my palm under the system PalmOS Devices, and sync using WIFI.

The only thing I have noticed is that if I reboot/shutdown the computer, I have to go into the settings for the PalmOS Devices and edit the device and under device ID select get ID from Device, once that is complete then I am able to sync when ever I want until the next SD or reboot.

it appears to me that everything is working fine, PRC, PDB file are backed up and contact information and Schedules are incorporated into Evolution.

I have not found out yet how to transfer documents from my palm to comp and vice versa.

---

### Post by Robin50 on 2007-12-19
I'm just over 2 weeks old with linux, loving it so far but reading your posts is like another language. I'd love to use jpilot but the system will only sync with evolution. This is the message I get when I try to sync with jpilot:

Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

Can someone help resolve this in easy to understand terms, thanks in advance

---

### Post by Shawn Reist on 2007-12-20
Hello,

I am relatively new to Linux also, but I am working things through...

What kind of Palm are you trying to connect and what method?  USB, Bluetooth or WiFi?

---

### Post by bgoody on 2007-12-24
Hi.  I'm pretty sure you have to disable gnome pilot before you can use J-pilot. On the J-pilot web site there is a link to their discussion group archives.  I'm sure you'll find the solution there but if it was me, I would just go into Synaptic an uninstall Gnome Pilot or whatever it is they call it.  It's really just a thingie to sync with Evoultion.


> **Robin50 said:**
> I'm just over 2 weeks old with linux, loving it so far but reading your posts is like another language. I'd love to use jpilot but the system will only sync with evolution. This is the message I get when I try to sync with jpilot:

Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

Can someone help resolve this in easy to understand terms, thanks in advance

---

