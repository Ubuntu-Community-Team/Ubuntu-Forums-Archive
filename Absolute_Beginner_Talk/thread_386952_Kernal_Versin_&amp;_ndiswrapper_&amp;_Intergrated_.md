---
title: "Kernal Versin &amp; ndiswrapper &amp; Intergrated broadcom 4306 on gateway m520"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by rdistiso on 2007-03-17
hey all im brand new to ubuntu like i just installed it i am currently running the updates i have a broad come wireless 4306 intergrated in my gateway M520 notebook it is now dual booted with XP home :(

i downloaded the NDISWRAPPER and i coppied the BCLWL5.sys file from my windows/system32/drivers directory to the desktop on ubunto i believe i am using 6.06 edgy its hard to tell

can someone tell me the steps i need to take and care fully explain how do get this wireless working

---

### Post by dbbolton on 2007-03-17
check this howto: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

let me know if it helps.

---

### Post by rdistiso on 2007-03-17
this is what i got when i ran the command below in one of the steps in contuined anyway with the rest of the step and ran modeprobe and i see the signal strength but still no connect i put the ssid in and no pasword cause there is none for the router let me know what you think need some more help

rdistiso@rdistiso-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys
Password:
bcm43xx-fwcutter can cut the firmware out of /home/rdistiso/Desktop/bcmwl5.sys


filename :  bcmwl5.sys

version  :  3.70.17.0

MD5      :  d87b4e14e890091d8e64fb5c570cf192

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...

extracting bcm43xx_microcode5.fw ...

*****: Sorry, it's not possible to extract "bcm43xx_microcode11.fw".

*****: Extracting firmware from an old driver is bad. Choose a more recent one.

*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.

*****: But this can be added in the future...

*****: Sorry, it's not possible to extract "bcm43xx_microcode13.fw".

*****: Extracting firmware from an old driver is bad. Choose a more recent one.

*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.

*****: But this can be added in the future...

extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...

extracting bcm43xx_initval01.fw ...

extracting bcm43xx_initval02.fw ...

extracting bcm43xx_initval03.fw ...

extracting bcm43xx_initval04.fw ...

extracting bcm43xx_initval05.fw ...

extracting bcm43xx_initval06.fw ...

extracting bcm43xx_initval07.fw ...

extracting bcm43xx_initval08.fw ...

extracting bcm43xx_initval09.fw ...

extracting bcm43xx_initval10.fw ...

---

