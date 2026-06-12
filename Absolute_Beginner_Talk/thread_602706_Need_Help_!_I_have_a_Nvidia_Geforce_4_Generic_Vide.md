---
title: "Need Help ! I have a Nvidia Geforce 4 Generic Video Card ! Not Working with Gutsy."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by new on 2007-11-04
Hey ... I just upgraded to Ubuntu Gutsy 7.10 ...and my Nvidia Geforce 4 Generic Card ..within the Screens and Graphics ...it is showing the i810 card ... and the Nvidia card at the bottom ...but when i put the monitor into the Nvidia card ..nothing happens !! i have the drivers enabled from the Restricted Drivers Manager !! but it still wont work ? please help me ! thank u !

---

### Post by Fred_E _krugar on 2007-11-04
Have you tried using Envy ?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install that then use it to uninstall the drivers then reinstall the drivers.

---

### Post by Pumalite on 2007-11-04
You can also download from Nvidia and follow the instructions:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by new on 2007-11-04
thanks for the quick reply ...i will try the envy ...and then try the nvidia website ! ...so u think that the drivers within the restricted drivers manager werent right ??

---

### Post by Fred_E _krugar on 2007-11-04
could just be a bad install that is all.

---

### Post by Chymera on 2007-11-04
you should try to avoid envy at any cost, it's evil :P

Nonetheless this  seems to be a very common problem, nvidia drivers on gutsy tend to not recognize the gfx cards :(

---

### Post by goslings on 2007-11-04
FYI
GeForce 4 Ti 4600 has no problems with 7,1 
regards

---

### Post by candtalan on 2007-11-04
> **Chymera said:**
> 
Nonetheless this  seems to be a very common problem, nvidia drivers on gutsy tend to not recognize the gfx cards :(
I am no expert, and have installed gutsy in machines which were wrongly seen as intel not nvidia. - I had to manually edit the file
/etc/X11/xorg.conf
so that the incorrect driver is replaced with an nvidia one, in my case
nv
I used command line use of Vi editor - a bit of a struggle for inexperienced li'l ol' me
but it did work. I also left the text description as incorrect, (lazy) and this did not seem to matter (so far)

---

### Post by new on 2007-11-04
envy messed me up.... my onboard was working just fine...now it doesnt work either ...n the desktop effects dont activate anymore...n all of this use to work with my onboard video...sigh

---

