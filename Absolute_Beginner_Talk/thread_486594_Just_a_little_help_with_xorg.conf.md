---
title: "Just a little help with xorg.conf"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Skneepa on 2007-06-28
Hi...What I need to do is to enable the composite option for my 7600GS video card as I disabled it while installing the NVIDIA drivers by misunderstading the NVIDIA guide :(...If I figure it out right all I have to do is to access xorg.conf and remove the words  "composite" "disable" or just replace it with "enable"...So what shall I do? Is this editing all that is needed or I have to set anything in NVIDIA settings as well? Here are the last lines of my xorg.conf :

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

---

### Post by overdrank on 2007-06-28
> **Skneepa said:**
> Hi...What I need to do is to enable the composite option for my 7600GS video card as I disabled it while installing the NVIDIA drivers by misunderstading the NVIDIA guide :(...If I figure it out right all I have to do is to access xorg.conf and remove the words  "composite" "disable" or just replace it with "enable"...So what shall I do? Is this editing all that is needed or I have to set anything in NVIDIA settings as well? Here are the last lines of my xorg.conf :

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

Hi, you can do this by using the command in terminal *gksudo gedit /etc/X11/xorg.conf* 
:popcorn:

---

### Post by Skneepa on 2007-06-28
Hi, thanks for your reply but I'm already familiar with the gedit command...What I'm not sure about are the lines I have to edit. How the last lines of my xorg.conf should be edited? Is it as simple as replacing "disable" with "enable"? Will that alone do the trick for me? After editing xorg.conf do I need to do other suff like editing NVIDIA settings? 

Sorry if I did not explain things right in my first post ;)

---

### Post by overdrank on 2007-06-28
> **Skneepa said:**
> Hi, thanks for your reply but I'm already familiar with the gedit command...What I'm not sure about are the lines I have to edit. How the last lines of my xorg.conf should be edited? Is it as simple as replacing "disable" with "enable"? Will that alone do the trick for me? After editing xorg.conf do I need to do other suff like editing NVIDIA settings? 

Sorry if I did not explain things right in my first post ;)

Ok yes just replace disable with enable and save. No we hope that it will solve your problem and no you should not have to edit anything else. :D

---

### Post by Skneepa on 2007-06-28
Ok, it worked after computer restarted...Now I have some other problems with desktop effects so I have to do a little more research in the forums! Anyway, thanks for all the help!:D

---

### Post by ruza on 2007-06-28
Hey ppl I need to ask you one thing. I want to change my refresh rate. But, I have installed restricted drivers and changing of xorg.conf does not seam to do anything. Is it possible that driver bypasses xorg.conf settings?

---

