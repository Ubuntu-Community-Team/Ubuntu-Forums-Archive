---
title: "Macbook 1,1 Ubuntu 12.04 Error"
date: 2012-05-04
forum: Apple Hardware Users
---

### Post by trivialpackets on 2012-05-04
When I start up, I'm getting an error, and it appears occasionally with the latest ubuntu 12.04.  

The error is:

Sorry, Ubuntu 12.04 has experienced an internal error and the details reveals

ExecutablePath:  /usr/share/apport/apport-gpu-error-intel.py

I'm not even really sure where to start, although I'm hoping to get this thing working.

---

### Post by trivialpackets on 2012-05-04
Disregard, I took the easy way out and installed Kubuntu 12.04 and all is working well.

---

### Post by deciocavallo on 2012-05-23
> **eric.proctor said:**
> When I start up, I'm getting an error, and it appears occasionally with the latest ubuntu 12.04.  

The error is:

Sorry, Ubuntu 12.04 has experienced an internal error and the details reveals

ExecutablePath:  /usr/share/apport/apport-gpu-error-intel.py

I'm not even really sure where to start, although I'm hoping to get this thing working.

Same error for me for a macbook 2.1, seems to be an video card driver error, but for me there's not any driver for Intel Gma 950.

With KUbuntu have you resolved the error?

---

### Post by philperrin on 2012-05-25
I just tried installing Ubuntu 12.04 on my Macbook 1,1 and have the same error. I will be trying Kubuntu 12.04 later today. 
I imagine it is not specific to the macbook model, since this error seems to be everywhere - just do a google search for ub (although I do suspect the graphics card-Intel GMA 950- is causing it on my machine).

---

### Post by deciocavallo on 2012-05-25
> **philperrin said:**
> I just tried installing Ubuntu 12.04 on my Macbook 1,1 and have the same error. I will be trying Kubuntu 12.04 later today. 
I imagine it is not specific to the macbook model, since this error seems to be everywhere - just do a google search for ub (although I do suspect the graphics card-Intel GMA 950- is causing it on my machine).

i like ubuntu but i don't like kde because it has not an index search (real time) :P

---

### Post by trivialpackets on 2012-05-25
I do not receive the error on kubuntu, but from what I was able to gather from reading on launchpad that this is a false positive from apport and I believe they were looking to at least band-aid it until version 12.10.  Overall, I really do like kubuntu, but it's not my preference.  I've actually settled on trying to sell the macbook and get a laptop that is more ubuntu friendly.  Someday, I'll get back to my unity!  Although I do run it on my development server @ home and on my vps.

---

### Post by philperrin on 2012-05-25
I can confirm - no startup errors on Kubuntu with macbook 1,1.

I like unity - it works nice... but errors (even false positives), are enough for me to switch to KDE... at least until those hiccups are figured out.

---

### Post by deciocavallo on 2012-05-25
> **philperrin said:**
> I can confirm - no startup errors on Kubuntu with macbook 1,1.

I like unity - it works nice... but errors (even false positives), are enough for me to switch to KDE... at least until those hiccups are figured out.


is possible in kde to switch to unity interface? or Gnome? 

and there is an app to do fast search app like in unity?

---

### Post by trivialpackets on 2012-05-27
It's not great, but you've got two options.  First, you can click into the menu and type.  That works.  The second option is that if you don't have an application in focus, you can Apple+space to bring up similar to what it does on OSX.

---

### Post by deciocavallo on 2012-05-29
i've installed lubuntu 12.04, no errors and is wonderful! 
fast!
Incredible! I like it so much!

---

### Post by FrancisIp on 2012-06-09
I have a MacBook 2,1 installed Ubuntu 12.04 same error

I followed the document on installing from CD to Mac
Skip the part where rEFIt need to sync partition table, 
as its already in sync.
 
you could be right might be a intel on-board graphics issue.
As I have Intel GMA 950 too

---

### Post by deciocavallo on 2012-06-09
> **FrancisIp said:**
> I have a MacBook 2,1 installed Ubuntu 12.04 same error

I followed the document on installing from CD to Mac
Skip the part where rEFIt need to sync partition table, 
as its already in sync.
 
you could be right might be a intel on-board graphics issue.
As I have Intel GMA 950 too

is a false error but is irritating, i think that fix it on next release, meanwhile, install lubuntu that is very fast!

---

### Post by raintheory on 2012-06-11
Same error on mine, would installing and using gnome reslove the issue?  Is it unity-specific?

---

### Post by Quenepas on 2012-06-22
Same error on triplebooted Macbook 4,1. Intel chipset i965g. Apport version 2.0.1-0ubuntu8. Arch amd64. SOme sort of GPU lockup. It happens sometimes but when it happens it reports the same thing over and over. Very annoying. Already reported thou :p

---

### Post by wpshooter on 2012-06-25
> **raintheory said:**
> Same error on mine, would installing and using gnome reslove the issue?  Is it unity-specific?

My "GUESS" is that yes it is, because when I installed MATE interface on my 12.04 installation and used the MATE interface this popup of internal error did NOT occur.

Ever who is responsible for this UNITY interface needs to FIX this !!!

Thanks.

---

