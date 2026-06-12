---
title: "[SOLVED] screwed up my graphics card driver.. help!"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by sourcemorph on 2007-12-09
ok here's this.. everything was running fine on my comp, desktop effects etc.. the video used to freeze a bit and the login window came at a lower resolution so i decided to upgrade my graphics card driver by envy.

it removed the nvidia-glx and nvidia-glx-new packages present on my comp and downloaded a fresh one from nvidia's website... it gave some error but i still continued with it, and then it asked to update hte xorg.conf file as wel... then when i restarted by comp was running in the low graphics mode, i changed the screen/graphics settings but it reverted back to the low settings. then i opened the restricted drivers manager and re-enabled the nvidia driver, and then changed the screen/graphics settings... it asked me to restart, it opened again in low settings and i again changed the screen/graphics settings but to no avail. when i open the restricted drivers manager, the nvidia driver is shown to be enabled but not in use.... whats that???

somebdy please help....

---

### Post by nikoPSK on 2007-12-09
Do this in recovery mode:

```
[SIZE=3]sudo dpkg-reconfigure -phigh xserver-xorg[/SIZE]
```

---

### Post by sourcemorph on 2007-12-09
hmm thats not working... i tried it.

btw i hav the nvidia 6150 controller, when im using the nvidia-glx-new drivers and i type "nvidia-settings" in the terminal i get the following error 

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

even after running "nvidia-xconfig" as root i get the same msg in nvidia-settings.

somebdy please help, the desktop looks terrible now after i hav lost all the desktop effects, widgets n dock....... [:(]

---

### Post by sourcemorph on 2007-12-09
k the prob is solved now.. i did a manual nvidia driver install with envy and things r fine now... lets see if these drivers are worth all the efforts... [:)]

---

### Post by nikoPSK on 2007-12-09
glad I could (somewhat) help. I didn't recommend envy to you though because I have had bad experiences with it.

---

