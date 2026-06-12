---
title: "How to Kill X-Servers n Open GL"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by kv_abhiram on 2007-09-08
Im currently installin my nvidia FX5500 drivers in my ubuntu
n it is askin to exit the X-servers and to kill the Open GL applications and this is what i found in nvidia.com HELP


**Prior to beginning the installation, you should exit the X server and kill all OpenGL applications (note that it is possible that some OpenGL applications persist even after the X server has stopped). You should also set the default run level on your system such that it will boot to a VGA console, and not directly to X. Doing so will make it easier to recover if there is a problem during the installation process. **


I would be happy to see ur reply

---

### Post by louieb on 2007-09-08
Ctrl+Alt+Backspace should kill X.
Booting to recovery mode will start Ubuntu in console mode and root as the owner.

---

### Post by kv_abhiram on 2007-09-09
what about Open GL applications ???

---

### Post by sumguy231 on 2007-09-09
If you're not running anything using 3d graphics, don't worry about it. If you are, I'd say still don't worry about it because it seems unlikely that any of them would stick around after you kill X.

---

### Post by kv_abhiram on 2007-09-09
how to boot into recovery mode

---

### Post by sumguy231 on 2007-09-09
When the bootloader says "Press Esc..." and gives a countdown, press Esc and select the recovery mode option.

---

### Post by Malibu Illusion on 2007-09-09
Ctrl+Alt+Backspace will restart it quickly.

```
sudo /etc/init.d/gdm stop
```

Will accomplish what you're looking for.

---

### Post by mysticmatrix on 2007-09-09
> **kv_abhiram said:**
> Im currently installin my nvidia FX5500 drivers in my ubuntu
n it is askin to exit the X-servers and to kill the Open GL applications and this is what i found in nvidia.com HELP


**Prior to beginning the installation, you should exit the X server and kill all OpenGL applications (note that it is possible that some OpenGL applications persist even after the X server has stopped). You should also set the default run level on your system such that it will boot to a VGA console, and not directly to X. Doing so will make it easier to recover if there is a problem during the installation process. **


I would be happy to see ur reply

Isn't FX5500 supported by Restricted Manager??
If not I recommend you getting Envy script to install your drivers. Downloading manually and installing drivers is lot of headache....

---

### Post by kv_abhiram on 2007-09-09
how do i do that ???

---

### Post by kv_abhiram on 2007-09-17
how do i do that ????????

---

