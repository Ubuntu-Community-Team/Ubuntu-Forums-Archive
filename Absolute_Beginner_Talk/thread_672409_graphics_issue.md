---
title: "graphics issue"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by s7alk3r91 on 2008-01-19
i recently installed my Nvidia 8800GT driver (NVIDA-Linux-x86-169.07-pkg1.run) and apon reboot it said graphics card not detected and to select your monitor and graphic card in configure i did so 1680x1050 resolution and Nvidia Geforce 8 series it brought me to the login witch i was able to log in but its only giving me 800x600 resolution and when i open Nvidia X server settings it tells me to run  nvidia-xconfig and after doing so restart the x server so i opened up terminal typed nvidia-xconfig and it sayed 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

i dont know how to restart the xserver i tryed CTRL ALT backspace and i still got the same thing can someone please help?

i also tryed choosing the graphic configuration in System>Administration>Screen and Graphics it had me log off and asked me to choose again then i went back tot he login screen and it was still 800x600 and still needed to run nvidia-xconfig

graphics card=Nvidia 8800GT
monitor = Samsung 2220WM 22 in 1680x1050

---

### Post by Ub1476 on 2008-01-19
Try to use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to remove the driver you just install, then let it install the driver itself and configure the xserver for you. The reboot.

To run Envy type:

```
envy -g
```

---

### Post by s7alk3r91 on 2008-01-19
i got envy removed the driver then i went to install it and i got ENVY ERROR: Envy dose not recognize your card as compatible with any version the driver. this might happen because either your card is not supported by the driver or Envy's Harwaredetection failed you can try the manual installation at your own risk

---

### Post by Ub1476 on 2008-01-19
I just read a post, where a person succeeded by installing the manual way on his 8800GT, choosing the latest driver. I don't know if Envy will configure your xserver when installing manually, but I would give it a chance:)

```
envy -t
```

---

### Post by s7alk3r91 on 2008-01-19
alright im trying it ill let u know the results

---

### Post by s7alk3r91 on 2008-01-19
it had an automatic configure option and was successful upon restart even got the Nvidia logo thanks a bunch

---

### Post by Ub1476 on 2008-01-19
Glad to hear it worked:)

---

