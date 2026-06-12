---
title: "Is it a bug ???"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2007-09-07
Hello guys. I have installed ubuntu 7.04 on my laptop and many other laptops and desktops. On all of the installations after installation i reboot the comp and when linux starts the ubuntu logo comes and then after the  lower bar fills up by about a cm suddenly a text terminal opens and its says that the write and mount time on sda3 ( my partition which is the / partition of linux) is in the future. Then It fixes it. It then says that the partition is mount 49 thousand odd times without being checked ( though it was formated just before installing linux) . It then starts the check and when finishes it says reboot linux and then says checksum returned exit status 1 with a red colour failed written on the right side. Then it displays some text that just flashes for a moment and then the computer reboots. After this first boot the next time  onwards it boots automatically without any problems. I have notice this on all the systems that i have installed ubuntu on.  Mine is an acer travellmate 4150, acer Aspire, Toshiba satelite, an assembled desktop with an intel core 2 duo with intel motherboard, hp nx 6125 and a few others. Hence i would like to now is this a problem or is it a new feature in ubuntu as i never had this in the previous ubuntu release. Hence could someone please  tell me if it is a bug or not and if it is then can the ubuntu team please make sure they fix it. 

Thanks

---

### Post by w4ett on 2007-09-07
This normally happens when:

1.  Bios system clock is set to the incorrect time and date.
or
2.  CMOS Battery is failing and/or dead.

I recommend that you check the above to cure the fault.

---

### Post by justleen on 2007-09-07
I think your <ENTER>  is bugged too.... ;)

---

### Post by mlentink on 2007-09-07
> **quarkhirad said:**
> Hence could someone please  tell me if it is a bug or not and if it is then can the ubuntu team please make sure they fix it. 

Seeing as how you were able to duplicate this on several dissimilar computers, it's certainly weird. On the other hand, Feisty has been with us for a while now, and this is the first time I heard about it. Could you tell us from which timezone you are? Have you taken a look at Launchpad yet?

---

