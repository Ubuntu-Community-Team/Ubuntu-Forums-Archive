---
title: "System sounds dont work anymore"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by calx on 2006-02-18
Hi,

When I first installed Ubuntu Breezy sounds worked fine, but for some reason now the only sound I get is when playing audio/video files or games. 

No system sounds; startup/shutdown, GAIM etc.

They are definitely enabled in the Sytem > Preferences > Sounds, but when I press the Test button they dont play then either. 

Playing the files in question e.g. /usr/share/sounds/gtk-events/activate.wav in totem works fine.

-Everything is unmuted in volume control.
-ran alsamixer and made sure everything is unmuted and turned up in there too.
-ALSA is selected for both Output & Capture in System > Preferences > Multimedia Systems Selector (Tests ok) switching to ESD doesnt make any difference. 

Im using a Dell Latitude CPx laptop with ESS ES1978 (Maestro 2E) onboard sound, running Breezy. :???: 

Any tips would be appreciated, thanks!

---

### Post by nalmeth on 2006-02-18
I'm pretty sure that esd controls all the system sounds you hear, in gnome anyway. The KDE equivalent is aRTs. Check your system monitor to see if there are multiple instances of this running (gnome) APPLICATIONS --> SYSTEM TOOLS --> SYSTEM MONITOR. If there are many running, kill the extras, and if they all get killed, hit ALT-F2 and execute esd. Or reboot.

---

### Post by calx on 2006-02-23
Thanks for the reply nalmeth.

Turns out it was the alsa drivers causing the problem, installing the esd lib returned it to normal.:)

---

### Post by LordBug on 2006-02-23
ALSA calls for a harware mixer to play sound from 2 different sources.  Most on-board sound chips don't have a hardware mixer.  ESD is a sound server.  It uses a software mixer to handle multiple sound sources.

---

### Post by calx on 2006-02-23
Thanks for clearing that up LordBug :)

---

### Post by billdoor on 2006-02-23
I have this problem too. It worked fine until one of the latest updates. Now, whenever something tries to play a sound in KDE I get the knotify error and usually the app crashes (such as kalarm).

Also if I try to change sound system in the KDE control panel, it never finishes the "starting sound system" progress bar.

---

### Post by LadyDoor on 2006-02-25
[QUOTE=calx]Thanks for the reply nalmeth.

Turns out it was the alsa drivers causing the problem, installing the esd lib returned it to normal.:)[/QUOTE]

Hi. So, a question:  which esd lib did you install to return it to normal? I already have libesdalsa0, but if the idea is to use the ESD instead of ALSA, then do I need to uninstall that somehow? If so, that is a concern, because when I try to install libesd0, it tells me it will uninstall not only libesdalsa0 but also the Ubuntu-Desktop package; when I tried first uninstalling libesdalsa0, it popped up a window (Synaptic, that is), telling me that doing this would require uninstalling (basically) every single graphical program I have installed. So does this mean that I should just accept that I can't have system sounds or 2 sounds at once, or is there a magic workaround or somesuch, or am I just looking in all the wrong places?

Thanks!
--Door

---

### Post by calx on 2006-02-26
Yes it seemed that installing libesd0 did the trick. But I did try installing a few different fixes for Skype, which still isn't working, which is when it must have broken.  So this worked for me, but I dont know if it will really do what it's threatening in your case.:confused: 

calx
 
[QUOTE=LadyDoor]Hi. So, a question:  which esd lib did you install to return it to normal? I already have libesdalsa0, but if the idea is to use the ESD instead of ALSA, then do I need to uninstall that somehow? If so, that is a concern, because when I try to install libesd0, it tells me it will uninstall not only libesdalsa0 but also the Ubuntu-Desktop package; when I tried first uninstalling libesdalsa0, it popped up a window (Synaptic, that is), telling me that doing this would require uninstalling (basically) every single graphical program I have installed. So does this mean that I should just accept that I can't have system sounds or 2 sounds at once, or is there a magic workaround or somesuch, or am I just looking in all the wrong places?

Thanks!
--Door[/QUOTE]

---

### Post by LadyDoor on 2006-02-26
Oh well, thanks anyway--it's not actually that big of a deal. I'm glad it worked for you though!

---

### Post by calx on 2006-03-20
Just wanted to add this for the record, I recently upgraded to Dapper and encountered the same problem, no system sounds.

apt-get install libesd0

Apt says.. 

The following packages will be removed

libesd-alsa0 ubuntu-desktop

I let it continue, system sounds returned immediately and the desktop remains..

So what does that mean? Why does it say it will remove ubuntu-desktop? 

Anyway I frickin love Ubuntu regardless! :-D

---

