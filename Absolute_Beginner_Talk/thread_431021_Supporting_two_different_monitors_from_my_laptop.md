---
title: "Supporting two different monitors from my laptop"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by msharelick on 2007-05-02
Hi:

I have not yet installed Ubuntu, so its not too late to fix any problem that I may create. 


I have a Dell 700M laptop.  I need to support two different monitors from it.  One, the monitor that I usually use which is attached to the machine.  The second one , I attach to video port when I am home is a Syncmaster 900NF.  A normal monitor.  Is it possible to setup Ubuntu to auto-detect which monitor to use?

I am also willing to log into Ubuntu in text mode and start a script which picks the right configuration. 

Thanks

Matthew Harelick

---

### Post by annda on 2007-05-02
hi!

first of all, you will need to install the video drivers for you graphic card. that will let you configure the monitors and create the appropriate xorg.conf files for them.

you can always change the xorg.conf by hand on boot, but someone has figured out how to create different boot options for different conf files. unfourtunately i have lost the forum thread. but it is possible.

---

