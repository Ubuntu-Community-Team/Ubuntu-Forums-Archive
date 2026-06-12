---
title: "Disabling usplash at boot?"
date: 2006-10-30
forum: Apple PPC Users
---

### Post by Senori on 2006-10-30
My laptop (Powerbook G4) has a problem that I suspect is coming from usplash by the way it's happening, which is making it impossible for me to boot it.

Is there any way to disable the splash from the yaboot prompt?

---

### Post by cmorgan47 on 2006-10-31
in /etc/yaboot

get rid of the line that says append="quiet splash"

then sudo ybin

optionally, you can get rid of the "quiet" and leave the "splash" to have it like dapper....splash + boot messages

---

### Post by Senori on 2006-10-31
> **cmorgan47 said:**
> in /etc/yaboot

get rid of the line that says append="quiet splash"

then sudo ybin

optionally, you can get rid of the "quiet" and leave the "splash" to have it like dapper....splash + boot messages
I'm aware of that, but as I can't boot I'm unable to edit it (and I don't know how to access a failsafe mode using yaboot either).

---

### Post by seatea on 2006-10-31
If you can boot from a Live  CD, then you can mount your root partition and use ```
sudo gedit /<whatever your mountpoint is>/etc/yaboot.conf
``` to change the parameters.

---

### Post by Senori on 2006-10-31
> **seatea said:**
> If you can boot from a Live  CD, then you can mount your root partition and use ```
sudo gedit /<whatever your mountpoint is>/etc/yaboot.conf
``` to change the parameters.
Also regrettably impossible; the laptop has a slot-loading CD drive with a CD already in it, and the eject button (also the F12 button; thanks Apple!) doesn't seem to be recognized at this stage.

---

### Post by jediborger on 2006-11-01
Sorry I'm not a Mac person but I know from experience how to get a cd out of a slot loading drive. Take a safety pin and push it in on the right side of the slot, this should force the cd out. From there I assume you know to hold down the B key during boot to boot from CD.

---

### Post by APU on 2006-11-01
Another way to get the CD out of the drive is to hold down the trackpad button (or the left button of a connected mouse) while turning the Mac on. Just keep pressing it down until the CD slides out.

And it´s the "C" key which lets you boot from CD

---

### Post by cmorgan47 on 2006-11-01
have you tried fn+F12.  
seems to work during most stages of boot/shutdown on mine.

---

