---
title: "Dummy Output Lenovo chrombook 11e"
date: 2020-04-26
forum: Any Other OS
---

### Post by kacpers2002 on 2020-04-26
Hello
I have a big problem.Yesterday I installed Ubuntu on my chromebook and everything works fine but sound is not. Like I said earlier Dummy Output , I spent about 14h trying to fix it in all ways - nothing helped. I have updated everything , speakers are working on chromeOS and headphone jack too. What do you think about changing distribution ? Not based on debian ?


~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xd1314000 irq 315
 1 [chtrt5650      ]: chtrt5650 - chtrt5650
                      chtrt5650

---

### Post by tea for one on 2020-04-26
Is your device listed here?

[https://wiki.galliumos.org/Hardware_Compatibility](https://wiki.galliumos.org/Hardware_Compatibility)

If it is supported then you may have better luck.

---

### Post by kacpers2002 on 2020-04-28
Yes it's there. So I need to install GalliumOS?
[h=2][/h]

---

### Post by kacpers2002 on 2020-04-28
I changed system to GalliumOS and nothing happened - still dummy output

---

### Post by tea for one on 2020-04-28
Have you explored all the options for Custom Firmware detailed in the GalliumOS wiki pages?

[https://wiki.galliumos.org/Firmware](https://wiki.galliumos.org/Firmware)

As far as I understand it, Chromebooks are not always perfect companions for Linux distros and a certain amount of investigation/trial and error is required.

---

### Post by kacpers2002 on 2020-04-29
Problem solved
I changed seabios to coreboot by mrchromebook [https://www.howtogeek.com/278953/how-to-install-windows-on-a-chromebook/](https://www.howtogeek.com/278953/how-to-install-windows-on-a-chromebook/) but instead of installing win 10 I installed Popos (don't give up when u see some error doing boot for pendrive , u just need to wait a bit like 15min and all will be ready to install)

---

### Post by Frogs Hair on 2020-04-29
Moved to Any Other OS. Crouton or other installation methods are not supported by Chrome OS or Ubuntu.

[https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)

---

