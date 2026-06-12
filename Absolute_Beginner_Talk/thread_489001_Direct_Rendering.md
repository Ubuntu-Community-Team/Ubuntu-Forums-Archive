---
title: "Direct Rendering"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by NAT1V3 on 2007-06-30
How exactly do you enable direct rendering when i configured my x server i remember having it on i believe but i entered "glxinfo | grep direct" and it says no I'm confused before i changed my screen resolution to 1280x1024 from 1024x768 it said yes. Thanks in advance, Brad

---

### Post by overdrank on 2007-06-30
> **NAT1V3 said:**
> How exactly do you enable direct rendering when i configured my x server i remember having it on i believe but i entered "glxinfo | grep direct" and it says no I'm confused before i changed my screen resolution to 1280x1024 from 1024x768 it said yes. Thanks in advance, Brad

Hi can you tell us what video card you are using?

---

### Post by NAT1V3 on 2007-06-30
ATI Radeon x300

---

### Post by overdrank on 2007-06-30
> **NAT1V3 said:**
> ATI Radeon x300

Ok try this command in the terminal
[PHP]sudo dpkg-reconfigure -phigh xserver-xorg [/PHP]
And answer a few question and then select the resolution you want.
hope this helps good luck!

---

### Post by NAT1V3 on 2007-06-30
Hmm nothing if i clean install then run envy i have direct rendering at 1024x768 someone told me put this in "sudo dpkg-reconfigure xserver-xorg" i have to go to a blue screen select some options and choose 1280x1024 then i enter "glxinfo | grep direct" and get the return "no" even if i go back to 1024x768  still "no" so i have to clean install and try again for i don't know how to reset all the damage I've done I've tried about 5 times now to no avail does any one know what to do the card is capable of running aero just fine I don't know why it isn't capable of "direct rendering" any help would be greatly appreciated, Brad

---

### Post by overdrank on 2007-06-30
> **NAT1V3 said:**
> Hmm nothing if i clean install then run envy i have direct rendering at 1024x768 someone told me put this in "sudo dpkg-reconfigure xserver-xorg" i have to go to a blue screen select some options and choose 1280x1024 then i enter "glxinfo | grep direct" and get the return "no" even if i go back to 1024x768  still "no" so i have to clean install and try again for i don't know how to reset all the damage I've done I've tried about 5 times now to no avail does any one know what to do the card is capable of running aero just fine I don't know why it isn't capable of "direct rendering" any help would be greatly appreciated, Brad

I have the same card on my desktop and you dont have to reinstall again. Just edit you xorg where the driver section is make sure it is  "ati" and in the monitor section add the resolution that you want to each line.

---

### Post by NAT1V3 on 2007-06-30
so in theory once this clean install completes if i run envy then add 1280x1024 to my xorg file i will be able to select 1280x1024 and still have direct rendering (im trying to enable desktop effects)? by the way to i push alt+f2 "gksudo nautilus" and file down to xorg.conf and just edit it from there or do i have to do something in the command prompt?

---

### Post by overdrank on 2007-06-30
> **NAT1V3 said:**
> so in theory once this clean install completes if i run envy then add 1280x1024 to my xorg file i will be able to select 1280x1024 and still have direct rendering (im trying to enable desktop effects)? by the way to i push alt+f2 "gksudo nautilus" and file down to xorg.conf and just edit it from there or do i have to do something in the command prompt?

Yes in the terminal enter
[PHP]gksudo gedit /etc/X11/xorg.conf[/PHP]

---

### Post by NAT1V3 on 2007-06-30
okay i'm going to try it when i get back on monday thanks for the help this is the easiest linux distro i've ever used and it installs in about 8 minutes which is even faster than the 18 min vista install which is simply amazing (given it doesn't have all the bloated features). Thanks again, Brad

---

