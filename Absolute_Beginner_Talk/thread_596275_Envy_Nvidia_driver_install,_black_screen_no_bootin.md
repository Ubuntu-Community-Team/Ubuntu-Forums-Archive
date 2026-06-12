---
title: "Envy Nvidia driver install, black screen no booting"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by jd3010 on 2007-10-29
I just used the ENVY script to install a Nvidia driver.... install worked fine, but I just have a black screen, no booting, nothing ...

is there a way to boot in Safe mode with a graphical interface ?

I think that the driver whci got installed is probably too new for my PC, I would nee dto install an earlier version. Is there a way to copy an older version to somewhere. OR at least is there a way to undo what I just did ??

thanks

---

### Post by taurus on 2007-10-29
Boot into recovery mode from GRUB menu and at the prompt, edit your /etc/X11/xorg.conf

```
nano -Bw /etc/X11/xorg.conf
```
and replace the "**nvidia**" with "**nv**" under the Driver section.

Save it with <Ctrl>o and exit with <Ctrl>x and reboot.

```
shutdown -r now
```

---

### Post by jd3010 on 2007-10-29
> **taurus said:**
> Boot into recovery mode from GRUB menu and at the prompt, edit your /etc/X11/xorg.conf

```
nano -Bw /etc/X11/xorg.conf
```
and replace the "**nvidia**" with "**nv**" under the Driver section.

Save it with <Ctrl>o and exit with <Ctrl>x and reboot.

```
shutdown -r now
```
Woahhh, thanks a lot ....

I do have the graphical interface again. How can I copy over the good driver? I it a matter of just copying over the correct version (glx-generic 71) ??? or what should I do ??

thanks a lot I just strted with Linux and Ubuntu

---

### Post by taurus on 2007-10-29
Have you tried to install nVidia driver with the one that comes with your machine, System -> Administration -> Restricted Drivers Manager?  What model is your nVidia card anyway?

---

### Post by jd3010 on 2007-10-29
yes is the same newer version GLX-new version 91 ... an I had the same problem...

Must admit that I am a bit stuck here ... I can manually install the package from Synaptec PM but I am not sure if it is installed or not ....

Do wyoui think that it might be just a matter of configuring the xorg.conf file ??

---

