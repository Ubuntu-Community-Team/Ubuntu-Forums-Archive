---
title: "view screen on TV problem"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Ceta on 2007-02-11
In windows I would go to display properties and would be able to flip my desktop to my tv so that i could watch shows on my tv via my computer's dvd player.  How do I flip the display over to my TV with Ubuntu 6.10?

---

### Post by fenian on 2007-02-11
Do you have an Nvidia card with the latest drivers?If you have an Nvidia card but need the latest drivers use Envy to get the drivers...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

After you install the drivers and are logged back into Ubuntu open a terminal and type

> sudo nvidia-settings

This will open the nvidia settings window.Go to the X server display configuration section if both displays aren't shown click detect displays select the TV and click the configure button choose seperate X screens set the resolution (640x480 for non hdtv).Click the save to X configuration file button.Exit and restart X (ctrl+alt+backspace)

---

### Post by Ceta on 2007-02-11
I have a radeon card with the latest drivers.  I just cant find the displau option to flip the desktop over to the tv instead of the monitor.

---

