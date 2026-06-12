---
title: "How do you tell what NVIDIA driver you have installed?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by ironfistchamp on 2006-10-17
Hey all

This may sound totally stupid but how can I tell what Nvidia Driver is currently in use. I just installed the Nvidia Beta driver and got an error about modular X.Org but it went through and told me it was installed. I restarted X and there were no problems. I just want to check that it is acutally using the driver I just installed and not the free one from the repositories. I can't just accept that it has worked as it never "just works" for me. I have to try it at least twice to get it.

Thanks

Ironfistchamp

---

### Post by bodhi.zazen on 2006-10-17
first you will see the nVidia logo if the nVidia drive is installed.

Second re-run the installer. You will get a message re current nVidia drive, do you wish to proecce. Just say no.

---

### Post by PriceChild on 2006-10-17
grep "NVIDIA X Driver" /var/log/Xorg.0.log

---

### Post by Dual Cortex on 2006-10-17
going to the terminal and typing: nvidia-settings may help to... if nothing shows up then they are most likely not installed.

---

### Post by xpod on 2006-10-17
Ive insatalled them in dapper(both gnome & kde)
and have the beta`s here in edgy and they all show a nvidia logo at boot up.

Plus you should have an nvida settings option in your system tools menu.

I can look and see i`m apparently using 1.0-9625....

---

### Post by bdb on 2006-10-17
*I am pretty new to linux myself so this may be horribly wrong*

Type this in the terminal:```
less /etc/X11/xorg.conf
```

Click page down until you see the Device section.  If the driver says "nvidia" then the x server is using the binaray driver.

---

### Post by ironfistchamp on 2006-10-17
Thanks for the replies people. Ok so nvidia-settings shows a very bare menu. I seem to remember when using other binary drivers that there was more to the list. Is this just because it is beta? There is no logo but it is installed and xorg.conf shows nvidia as the driver.

Now that we have that sorted lets see if I can get Beryl and that installed.

Thanks again

Ironfistchamp

---

