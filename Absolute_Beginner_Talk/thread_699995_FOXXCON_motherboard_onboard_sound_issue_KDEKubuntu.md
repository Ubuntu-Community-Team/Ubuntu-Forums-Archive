---
title: "FOXXCON motherboard onboard sound issue KDE/Kubuntu"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2008-02-17
First of all, is there a method on KDE/Kubuntu to scan my motherboard so I know exactly what I have?  With that nest of wires in there I don't want to have to remove it just so I can get the model numbers.  I know it's a FOXXCON, and everything including the sound and video is "onboard"

That out of the way,   I loaded KDE/Kubuntu onto this system (new build out of scrap parts as a gift for a disabled friend) however I have no sound.

I run Kmixer and it says "mixer cannot be found" and shows a speaker with a slash through it in the status area.

Amarok...  displays "Audio output unavailable device is busy/Xine parameters:"  (just like that),,,, and does nothing.

SO!  Where to begin?  I know more about Gnome than KDE/Kubuntu at this point so I have no idea where to begin.   If it comes down to it I suppose I could disable the onboard sound and install a spare sound-blaster I have though I would really really like to get the onboard sound running so I don't have to move boards between systems.

---

### Post by Shazaam on 2008-02-17
Go to Applications>Accessories>Terminal. Once that opens type this in.......
```
lspci
```
This code will print out your hardware info and we can go from there.

---

### Post by Epic Plecostomus on 2008-02-18
> **Shazaam said:**
> Go to Applications>Accessories>Terminal. Once that opens type this in.......
```
lspci
```
This code will print out your hardware info and we can go from there.

Ok, I'll do that after work tonight.    

I'm also having demounting issues when shutting down.   When I click Shutdown I get a stream of error messages including one about unable to list all IDE devices/filesystem unable to demount or something to that effect.   

How do I grab the shutdown screens or dump all that text to a file for troubleshooting?


This is kind of frustrating,  Gnome-Ubuntu never had these problems even on this motherboard.

---

### Post by Epic Plecostomus on 2008-02-23
I have abandoned this project.   Too many issues to deal with.

Thanks for your help Shazaam.

---

