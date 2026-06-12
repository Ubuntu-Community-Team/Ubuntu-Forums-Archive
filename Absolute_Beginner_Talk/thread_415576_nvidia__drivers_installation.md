---
title: "nvidia  drivers installation"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by mekereke on 2007-04-20
When installing the nvidia drivers, the manual ask me to boot the kernel into runlevel 3...

 How to??
thanks

---

### Post by steve.horsley on 2007-04-20
Don't bother - that doesn't behave the same as Red Hat and so it won't help. 

Is there any reason you want the drivers from the nVidia site rather than the ones in the Ubuntu repository? If not, I suggest that you just use synaptic (System->Administration->Synaptic) and search for "nvidia". Install nvidia-glx (or nvidia-glx-new if you are on Feisty).

If there is a reason for installing the drivers from the nVidia download site, try this:
* Use synaptic to install package build-essential
* Use this command in place of changing runlevel to kill the X server:
**sudo /etc/init.d/gdm stop**
Log in, then get full privilege with this command:
**sudo su**
then run the install script, then restart X with
**/etc/init.d/gdm start**

Good luck

---

### Post by kpkeerthi on 2007-04-20
Install the driver from ubuntu repository. Instructions here [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Dyegov on 2007-04-20
They installed automatically for me, once I tried to enable the Desktop Effects. No problems at all :)

---

