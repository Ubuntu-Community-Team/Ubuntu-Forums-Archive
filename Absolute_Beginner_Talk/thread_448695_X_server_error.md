---
title: "X server error"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by xxvidelxx on 2007-05-19
Hello everyone, I am new to Linux and am trying to install Ubuntu 7.04 dektop and after installing I am receiving an error with xwindows. 

My assumption would be that although it recognizes my video card, it is not correct in the xorg.conf file. But..again..I'm new to Linux and need your advice as I am not too sure.

I turn on computer..I see ubuntu loading screen. It starts loading then I get a message saying:

"Failed to start the X server (your graphical user interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

"so then I chose yes and it states the warning:  (WW) I810: No matching Device section for instance (BusID PCI:0:2:0) found"

So if I then just continue it disables X server and goes to command line. I login and open /etc/X11/xorg.conf in vi editor. It shows my intel inegrated graphics card and not my nvidia geforce card. What do I need to change to make this work correctly? (as I am not very familiar with linux and what I would need to edit in this config file exactly) If that is indeed the problem as I suspect. If it is not the problem..Can anyone tell me why I am receiving this error? I'd send the config file but I'm on my windows laptop and I'm installing this on my desktop at the moment.

---

### Post by taurus on 2007-05-19
You need to go into the BIOS and turn off your onboard Intel graphic card controller.  Then, reconfigure your X again for nVidia graphic card with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xxvidelxx on 2007-05-19
I have a Dell Dimension 3000 and I do not see an option in my bios to turn this off. Is there any other way around this?

---

