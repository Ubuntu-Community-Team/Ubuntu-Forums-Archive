---
title: "Mcbook 5-3 Touchpad out of work"
date: 2010-09-12
forum: Apple Hardware Users
---

### Post by RugbyGandalf on 2010-09-12
Hello,

today i re-setup my system for my MacBook Pro 5-3 with Ubunto 10.04 lucid...
i walked through the configuration tutorial on [https://help.ubuntu.com/community/MacBookPro5-3/Lucid#Sensors](https://help.ubuntu.com/community/MacBookPro5-3/Lucid#Sensors)

but now i have the following problem: my touchpad won't work any more or react neither...

i run the following command:

sudo apt-get install dkms wget [http://launchpadlibrarian.net/24871974/bcm5974-dkms_1.1.4_all_test.deb](http://launchpadlibrarian.net/24871974/bcm5974-dkms_1.1.4_all_test.deb) sudo dpkg -i bcm5974-dkms_1.1.4_all_test.deb sudo modprobe -r bcm5974 sudo modprobe bcm5974

thought it would be a script for the touchpad - instead it removed my drivers for it...
does anyone know how to get my touchpad work again?

thank you very much

RugbyGandalf

---

### Post by wwwproperties on 2011-02-02
Wow that sucks dude! 

Have you tried googling this question? Hope you get it going again!!

---

