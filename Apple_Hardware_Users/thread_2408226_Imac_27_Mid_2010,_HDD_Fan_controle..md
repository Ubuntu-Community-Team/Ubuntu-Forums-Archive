---
title: "Imac 27 Mid 2010, HDD Fan controle."
date: 2018-12-15
forum: Apple Hardware Users
---

### Post by Renosam on 2018-12-15
Hello all.

First im new to Linux :)

I have an Imac Mid 2010, i use it as a plex server and to run som VM's when i need test enviroments.
I run Ubuntu 18 full installation.

I have changed my HDD to an SDD and now the HDD fan is at 100% all the time. In macos/OSX i used Macs Fan controle software to controle the fan speed.

I have been on google and done diffrent solution many hours the last few days.. i simply cant find a way to deal with this.

Pwmconfig change but i cant. when i try to run it i get this error.[COLOR=#444444][FONT=&amp]*/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed.*
[/FONT][/COLOR]So i added [COLOR=#444444][FONT=&amp]*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_enforce_resources=lax"* to [/FONT][/COLOR][B]/etc/default/grub.
[/B]But after a sudo update-grub and a reboot i get the same error.

I hope some of you guys have a solution, or maybe even been in this situation and got a fix :)

i have been follow this post. [https://iandw.net/2014/10/12/fancontrol-under-ubuntu-14-04-resolving-usrsbinpwmconfig-there-are-no-pwm-capable-sensor-modules-installed/](https://iandw.net/2014/10/12/fancontrol-under-ubuntu-14-04-resolving-usrsbinpwmconfig-there-are-no-pwm-capable-sensor-modules-installed/)

---

### Post by wildmanne39 on 2018-12-15
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by Renosam on 2018-12-18
Thanks :) didnt even notice there was an Apple hardware forum.

---

### Post by Renosam on 2018-12-18
Anyone know if i would be able to run Mac fan controle, or some windows software with Wine ? 

Im getting desperat the fans spins with 5500rpm,  way to much noise for the placement of the server in my house. Really dont want to go back to Macos.

---

### Post by gsahli on 2018-12-18
I haven't found anything as functional as MacsFanControl.
I guess you didn't re-use the temp sensor from the hard drive on the SSD?

---

### Post by kevin160 on 2018-12-19
This is a common problem with some imacs.  The Apple HD you removed had a special sensor in it, and your new SSD is missing that sensor.  You can buy a cable (from OWC and other sources) that will give you a sensor, or you can simply short the pins on the sensor cable you already have.  I don't have your model of mac, so definitely do some more research on this.  

For fan control software under Ubuntu, I use macfanctld.  There is also mbpfan.

---

### Post by Renosam on 2018-12-22
Thank you :) will take a look at the software.

Short the pins on the sensor.. i haven't really been thinking about that :) i will do it if the software cannot handle it.. otherwise i might have to install Macos again to make it quiet, and then make a new build when i got time for that.

---

