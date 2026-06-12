---
title: "Screen saver"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-09-14
All my screen savers are running 'jumpy'. The images come on the screen, but none of them are anywhere near moving fluidly. Is there a driver I can install to clear this up?

DVD's play fine, and everything else that requires movement (downloading progress bars, web-page scrolling,etc.) are perfect.

BTW--NVidia graphics card with...128 MB? (from about 4 years ago)

---

### Post by orb9220 on 2006-09-14
Do you have the nvidia drivers installed?

---

### Post by Imsati on 2006-09-15
I downloaded them, yes, but it didn't automatically install and I'm not certain how to go about with that.

---

### Post by bswilson on 2006-09-15
Installing the legacy NVIDIA video drivers

(Taken from [http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html))



1) Download and install the deb package:

[http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb](http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb)

2) Log out and press CTRL+ALT+F1 (so as to get out of the Desktop Environment, i.e. you'll see ONLY the command line)

3) Log in (if required)

4) Run "envy" by opening Terminal or Konsole and typing (quite obviously):

$sudo envy


5) Choose to install or uninstall the driver (from the textual interface)

---

### Post by Imsati on 2006-09-15
Still nothing. I also tried all the nvidia stuff from the repositories as well.

---

### Post by Imsati on 2006-09-15
The card itself is from about 4 years ago. I recently upgraded my MoBo and swapped it over so the MoBo wouldn't 'steal' memory for graphics. Maybe it's just time for a newer model?

NVidia Geforce 400 currently, 128 MB.

EDIT: some of them are fine. It's the more 'sweet factor' intensive ones that are jumpy (flux, gravity, etc. (The really cool ones:-) ).

---

