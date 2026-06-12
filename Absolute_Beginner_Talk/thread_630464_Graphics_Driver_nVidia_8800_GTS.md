---
title: "Graphics Driver: nVidia 8800 GTS"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-12-03
Did a bit of searching, didn't find a straight answer.
I remember awhile ago there was a script "Envy" that was the recommended method for installing GFX drivers from nVidia.  is that still true?  If so, where can I find it (doesn't come up in synaptic).

The other option is getting the driver directly from nVidia ... the link I've got to their AMD 64 bit linux driver is:
[http://www.nvidia.com/object/linux_display_amd64_100.14.19.html](http://www.nvidia.com/object/linux_display_amd64_100.14.19.html)

... this is a .run file.  I'm not sure what that is or if I should try to install it.  Any help for a noob?

---

### Post by FuturePilot on 2007-12-03
Are you using Gutsy? If so, just use the Restricted Driver Manager.
System>Administration>Restricted Driver Manager

---

### Post by aktiwers on 2007-12-03
This is how you install them manually:

Go here and download the latest 64bit driver:
[http://www.nvidia.com/object/linux_display_amd64_100.14.19.html]("http://www.nvidia.com/object/unix.html")
(here is the main link [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html))

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1
Log in
 type:
```
cd Desktop
```
```
sudo /etc/init.d/gdm stop
```And then
```
sudo ./NVIDIA-Linux-x86_64-100.14.19-pkg2.run
```when done.. type:
```
sudo reboot
```Edit:
Sorry..  just fixed the links and forgot one command.

---

### Post by atraeyu on 2007-12-03
> **FuturePilot said:**
> Are you using Gutsy? If so, just use the Restricted Driver Manager.
System>Administration>Restricted Driver Manager

Gutsy, Yes!

---

### Post by atraeyu on 2007-12-03
> **FuturePilot said:**
> Are you using Gutsy? If so, just use the Restricted Driver Manager.
System>Administration>Restricted Driver Manager

Whoa.  That was easy. Now to get compiz running!

---

