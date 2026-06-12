---
title: "Installed ATI driver, now what?"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-17
I've installed it but know I need to tell X to use the driver. I did it before but I've forgotten how i did it. I just basically selected which driver should be used in the Terminal.

---

### Post by Sokraates on 2005-12-17
Here's the command you want:

```
sudo dpkg-reconfigure xserver-xorg
```

Then you need to select "fglrx" as driver, not "ati".

---

### Post by Rackerz on 2005-12-17
Wont that make me have to reconfigure the xorg file? I don't like doing that because some of the options i choose and are incorrect so some settings change.

---

### Post by eMuNiX on 2005-12-17
If you don't want to re-run xserver-xorg then simply edit your /etc/X11/xorg.conf file changing "ati" to "fglrx" instead.  Then either restart the x server or reboot the machine and it should be good to go.

---

### Post by Rackerz on 2005-12-17
[QUOTE=eMuNiX]If you don't want to re-run xserver-xorg then simply edit your /etc/X11/xorg.conf file changing "ati" to "fglrx" instead.  Then either restart the x server or reboot the machine and it should be good to go.[/QUOTE]

I just did that however, in the OpenGL vendor string, renderer string and version string it fails to state anything, it just says 'unavaliable'. Before it did not say this. Also the transfer mode is 'PCI' is there anyway to change this to AGP?

Thanks

---

### Post by mlomker on 2005-12-17
I assume you've installed the two fglrx packages already.  I have a [how-to]("http://ubuntuforums.org/showthread.php?p=408111") for both drivers but it doesn't sound like you want to follow them.

---

