---
title: "Enforcing Screen Resolution"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by BoSchafers on 2005-09-22
My main Ubuntu server is located in the broom cupboard. It has no monitor. I manage it via VNC terminal (Remote Desktop). This all works quite well, except in the case of a reboot. Ubuntu loads with the lowest of screen resolution, presumably because it cannot detect the monitor i.e. there isn't one.  The low resolution makes it difficult to work with.

Is there a way way of forcing Gnome to load a certain resolution on startup.

TIA,
Bo

---

### Post by Knyven on 2005-09-22
I also have same problem, after i finished playing Call of Duty united offensive, when i go back to desktop, my resolution reset to 85hz (originally 75).

So what i did is i check the box "Make this default for this ()only". Now after finishing the game it goes back to normal.

---

### Post by BoSchafers on 2005-09-23
[QUOTE=Knyven]So what i did is i check the box "Make this default for this ()only". Now after finishing the game it goes back to normal.[/QUOTE]

Hmmm....

Thanks for the response Knyven. I've tried ticking that option, however as soon as I reboot the resolution is back to 480x?.

The only way to get it back to 1280x1024 is to hook up the monitor while booting, then disconnect it and avoid rebooting. 

There must be a better way. Anybody know how to enforce 1280x1024 resolution even when booting without a monitor?  :-? 

Bo

---

### Post by fordfan753 on 2005-09-23
In /etc/X11/xorg.conf it has a list of things like:
  ```
SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480" "1x1"
        EndSubSection

```
Try getting rid of all the other resolutions apart from the one you want to use, this should force it to use the only resolution you have entered. Be sure to do this for all depths.

---

### Post by herrpoon on 2005-09-23
That's the exact same problem I have!  I tried editing the Xorg.cong file to include only the resolution I wanted, but after boot-up without a monitor I still get stuck in some awful resolution.  I think this is more to do with, as you say, ubuntu obviously recognising that there's no monitor connected so decides to just go back to the lowest resoltuion possible.

Edit: I suppose there's always the possibility I did it wrong, I'd be interested in what happens when you try that.

---

### Post by BoSchafers on 2005-09-23
[QUOTE=herrpoon]T I'd be interested in what happens when you try that.[/QUOTE]

Prolly did something wrong also 'cause that didn't work for me.  ;-)  

(On the one hand its pretty brilliant the way the OS seamlessly detects most hardware by probing. In this case however the brilliance becomes a nuisance.)

For the sake of  all of us wishing to do remote server admin from the GUI, I dearly wish there was an enforced screen resolution option that worked **with and without monitor**...

Bo

---

