---
title: "Nvidia settings"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ep3w on 2007-06-05
I have my nvidia driver installed properly...as far as i know..everything seems to work fine.  When i go to change the nvidia settings in the GUI, specifially the digital vibrance and the image sharpening it works fine.  But when the reboot, those setting arent applied.  If i open the nvidia settings GUI again, the digital vibrance will come back without me changing it, just by opening the GUI.  Any way to get them to be applied when i reboot without opening the GUI?

---

### Post by khardbored on 2007-06-05
I would love an answer to this as well. I have the same issue, just with gamma. It works fine for the entire session but once I reboot I have to open/close the settings to get it take again. Very annoying.
6800..

---

### Post by khardbored on 2007-06-05
No one has any idea? Sniff.

---

### Post by forestpixie on 2007-06-05
You need to do 

sudo nvidia-settings 

in terminal to get it to change I think.

I'd backup as well just in case

---

### Post by ep3w on 2007-06-06
When i do sudo nvidia-settings it brings up the nvidia settings GUI and it has all the settings i specified before.  but when i tell it to save to x config file, this pops up in the terminal:
ryan@ryan-laptop:~$ sudo nvidia-settings

ERROR: Unable to determine valid vertical refresh ranges for display device
       'Seiko' (GPU: Quadro FX 350M)!


ERROR: Failed to add display device 'Seiko' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

do i need to manually edit it in xorg.confg? what ones do i edit to change the digital vibrance and image sharpening?

---

### Post by mkoehler on 2007-06-06
Make sure you're running it as a root user (sudo/gksudo) and you're not only pressing apply, but pressing "Save to xorg.conf file" as well.  However, my settings weren't being saved after doing that, so I decided to manually edit my xorg.conf file, it isn't that hard.

---

### Post by mkoehler on 2007-06-06
Just make sure that you make a backup or only make a few changes at a time before restarting X (to make sure you don't damage things beyond repair).

---

### Post by Crafty Kisses on 2007-06-06
> **ep3w said:**
> When i do sudo nvidia-settings it brings up the nvidia settings GUI and it has all the settings i specified before.  but when i tell it to save to x config file, this pops up in the terminal:
ryan@ryan-laptop:~$ sudo nvidia-settings

ERROR: Unable to determine valid vertical refresh ranges for display device
       'Seiko' (GPU: Quadro FX 350M)!


ERROR: Failed to add display device 'Seiko' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

do i need to manually edit it in xorg.confg? what ones do i edit to change the digital vibrance and image sharpening?
You can try recovering your X Server file.

---

### Post by ep3w on 2007-06-06
I looked at xorg.config but i dont know what part to edit to change the digital vibrance or the image shapenining.   i dont want to just start changing things at random....everything else is working fine besides the fact that it doesnt save the settings when i reboot.

---

### Post by Crafty Kisses on 2007-06-06
> **ep3w said:**
> I looked at xorg.config but i dont know what part to edit to change the digital vibrance or the image shapenining.   i dont want to just start changing things at random....everything else is working fine besides the fact that it doesnt save the settings when i reboot.

You should make a backup of your X Server file before making any changes, just a thought. :p

---

### Post by ep3w on 2007-06-06
> **Codename said:**
> You should make a backup of your X Server file before making any changes, just a thought. :p

first thing i did :D

---

### Post by Crafty Kisses on 2007-06-06
> **ep3w said:**
> first thing i did :D

You know how to recover it right? :p

---

### Post by ep3w on 2007-06-06
> **Codename said:**
> You know how to recover it right? :p

I find that out when i need too ;)

figured it out...in case anyone was wondering this worked for me
[http://ubuntuforums.org/showthread.php?t=310016&highlight=digital+vibrance](http://ubuntuforums.org/showthread.php?t=310016&highlight=digital+vibrance)
thanks for the help anyways :)

---

