---
title: "Openbox issue"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-10-07
Today i decided to try openbox instead of metacity. Searched for a couple of guides and started to follow step by step the indications. However, the first time i did "openbox --replace" in the terminal the window manager changed but this text appeared in the terminal:

fernando@Athena:~$ openbox --replace
I/O warning : failed to load external entity "/var/lib/openbox/debian-menu.xml"

(openbox:6830): ObParser-WARNING **: unable to find a valid menu file '/var/lib/openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/fernando/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:6830): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
I/O warning : failed to load external entity "/home/fernando/.config/openbox/menu.xml"

Also, when logged out and selected to start session with openbox (to make it the default WM) the OS freezes after i type my username and password and i need to reboot the system. Any tips?

---

### Post by mali2297 on 2007-10-07
> **ferpadro said:**
> 
Also, when logged out and selected to start session with openbox (to make it the default WM) the OS freezes after i type my username and password and i need to reboot the system. Any tips?

Are you sure that it freezes? Without configuration, the openbox session won't have any wallpaper or panels. Try to right-click with your mouse, you should get a menu from which you can at least launch a terminal.

---

