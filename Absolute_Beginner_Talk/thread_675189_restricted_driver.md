---
title: "restricted driver ?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by deadmnky on 2008-01-22
[I]i have an M2A-VM HDMI other board with an ATI Radeon x1250 graphics card. i just built the desktop and when i first installed ubuntu 7.10 i could only get an 800x600 display on the monitor. for some reason after installing envy i was able to get a smaller pixel resolution so now it looks ok. 
my question is basically i tried to enable my restricted driver (which is an ati accelerated graphics card) and somehow i got a message on the monitor saying cannot display this video mode.
i am pretty sure that the driver was not in use before but is now i was wondering if any one would know if i would get the same message if i tried to enable it now.
also wht would i have to do to enable the use of my dvi-d slot on my motherboard.
the monitor says in sleep mode hit any key to wake up. but doesnt wake up.
i am not sure what monitor i have it is a dell from 2001 i am borrowing it untill i can afford a lcd monitor next month.

if you could also explain what i did by installing and running envy so maybe i could give it a try manually next time that would help out as well

---

### Post by rax_m on 2008-01-22
Hi, not sure I can help with everything, but.. 

Basically the "restricted driver" is an ATI (or Nvidia) driver that gets installed from the repos. If you used Envy you also installed the ATI (or Nvidia) driver. You should not do both. As far as I know, Envy will use a more recent version of the driver compared to Ubuntu's restricted driver. 
If Envy works for you better than the restricted driver use it. BUT be aware that when it comes time to upgrade you may have to uninstall the Envy installed driver.

---

### Post by PeterJS on 2008-01-22
The way restricted driver work is like this. They are released under licenses that do not allow for redistribution, so Canonical can not install them by default (as this would require them to redistribute them, ie give them to you directly as part of the CD image). So the solution that they used for ubuntu is to set up packages (nvidia-glx and fglrx) that will download from the manufacturer and install the appropriate driver. The official deb packages tie specific version of the drivers to specific dists to conform to freeze deadlines and other testing conventions. What envy does is circumvent this process by directly grabbing and installing the newest driver. In addition to simply installing the driver, both envy and the restricted drivers manager try to reconfigure the system to use the device right away.

---

### Post by mikewhatever on 2008-01-22
Most of your questions are answered on envy's site, take a look [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).

---

### Post by deadmnky on 2008-01-22
so envy does all the work of downloading and installing the drivers assuming you dont have a cd.would it be the cd that came with the motherboard? it had some linux drivers on it i just didnt know how to install themor what ones to install, i dont remember what they were at present i can look it up. 
i am just asking to find a way to do it with out envy as it was the only thing i tried, other than trying to enable he driver initially. got a black screen on monitor heard the sound though so i know it booted.
and this being a new computer i know things had to be set up initially.

---

### Post by PeterJS on 2008-01-22
> **deadmnky said:**
> so envy does all the work of downloading and installing the drivers assuming you dont have a cd.would it be the cd that came with the motherboard? it had some linux drivers on it i just didnt know how to install themor what ones to install, i dont remember what they were at present i can look it up. 
i am just asking to find a way to do it with out envy as it was the only thing i tried, other than trying to enable he driver initially. got a black screen on monitor heard the sound though so i know it booted.
and this being a new computer i know things had to be set up initially.

Envy doesn't operate on the assumption that you don't have the drivers (not exactly, that is one part of it, but no body just has the drivers lying around so the same could be said of any install method), but rather that the testing procedures and safe guards put in place with the freezing and testing process are unnecessary and does it's own thing instead of using the stable drivers that the deb package would download.

With the exception of wifi and video drivers there's pretty much no need to install third party drivers, so I really wouldn't worry about installing them. The reason that video cards need the restricted drivers is because the manufactures (nvidia specifically) don't release the specs to the cards so the open source drivers are black box reverse engineered, and work incredibly well for what they are, but by definition probably will never give you 100% of the functionlity of the closed driver. ATI just recently, ie the last 6 months, released the specs for their cards which is forming the basis for the Radeon series of driver, but they aren't mature yet and cover a limted set of cards, so most people still use fglrx. For wifi it's alot of the same reasons plus some FCC regulations thrown in to gum things up.

---

