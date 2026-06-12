---
title: "screen resolution problem on update to 7.10"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by wog on 2007-11-11
If I have an nVidia FX5200 video card and a Sony SDM-HS94P monitor, why is it the update now has the upper limit on my screen resolution at 800 by 600 pixels?

And what do I do in order to fix this issue?

---

### Post by mike555 on 2007-11-11
I also have the 5200, I had to install Envy , and then install the driver though envy ........... you might need to use the command line if you can't use the desktop ...... not sure of the install command (check their website ) but after you get it installed restart and type " envy -t  " to get the text driver install .......

---

### Post by wog on 2007-11-11
So uninstall the driver and then reinstall it?

Is the latest version 0.9.7?

---

### Post by wog on 2007-11-12
Envy isn't working for me. It puts me in the same predicament I'm in now.

If I do an automatic install, envy ultimately gives me a black screen I can't get out of except to do Ctrl+Alt+F1 for a command line interface.

The options that get me to this position are manual install of legacy drivers, and even that wants me to run ```
sudo apt-get -f install
``` to clean up afterward.

Next suggestion?

---

