---
title: "Changed from ATI to nVidia graphic card"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by DMaT on 2007-06-01
Hi,
I had Ubuntu 7.04 installed on my computer with ATI Radeon X300 graphic card, and it work fine.
Recently I bought a brand new nVidia GeForce 8800 GTS card, after installing it I can't get Ubuntu even started, I get the "Failed to start the X server" massage and finally can get only to the terminal window.
My question is how do I install any working nVidia driver from terminal for at least to load Ubuntu normally?
Then I will think about installing newest or the best... I don't know, but first how do I boot it?

Thanks ahead...

---

### Post by renzokuken on 2007-06-01
when it gets to the "failed xserver" message, hit Ctrl+Alt+F1 to get to a tty terminal screen.

login and run

```
sudo dpkg-reconfigure xserver-xorg
```

follow the wizard leaving everything as it is (Default) until you get to the "driver" screen. select the "nv" driver. now continue on accepting the defaults.

do a ```
sudo reboot
```

and you should have grafix again. if "nv" doesnt work you can also use "vesa" in the meantime

now you may want to install the official nvidia driver, IMO, best done with Envy. [www.albertomilone.com](www.albertomilone.com) in the projects/guides section

---

### Post by arochester on 2007-06-01
You can reconfigure your xserver from the command line by using the command: >  sudo dpkg-reconfigure xserver-xorg
 This will start a text based wizard. Answer the questions you can. If there are questions you can't answer then go with the suggested default. If it doesn't work at firs then try again. You might have to specify VESA rather than ATI or Nvidia - but this should restart the graphics and you can load the specialist driver from there.

---

### Post by DMaT on 2007-06-01
Thank you guys I'll try...

---

