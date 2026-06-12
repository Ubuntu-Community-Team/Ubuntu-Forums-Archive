---
title: "Problems installing ubuntu"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Count de Monet on 2006-08-04
I'm having problems installing ubuntu.

The machine has a server motherboard - ASUS CUR-DLS with 2x1Ghz P111 cpu's. The motherboard has a Serverworks ServerSet III LE chipset with onboard 4MB ATI RAGE-XL graphics and 2x256mb ECC ram, 1x60Gb IDE HDD, 1xCDROM, 1xCDRW & a floppy drive.

When I start using the live CD the machine sometimes starts ok and the desktop is reached but then after a while the machine will freeze solid and I have to re-start. On a couple of ocasions on reaching the desktop I have clicked 'install' and all seems to go well until 25% of the installation is reached and then the machine again freezes.

I have tried the following opperating systems and ALL load and run fine:
Win98 SE
Windows 2000
Windows XP
Windows Server 2003

So why not ubuntu?

---

### Post by Drakkor on 2006-08-04
If you burned this disk,make sure you hit the second option:
2.Check CD for defects

---

### Post by kurniawands on 2006-08-04
> **Drakkor said:**
> If you burned this disk,make sure you hit the second option:
2.Check CD for defects

agree...... Drakkor is right... or see if your downloaded iso is fine.

---

### Post by Count de Monet on 2006-08-04
> **Drakkor said:**
> If you burned this disk,make sure you hit the second option:
2.Check CD for defects

Have done, it still freezes.

---

### Post by kurniawands on 2006-08-04
> **Count de Monet said:**
> Have done, it still freezes.

have you check if your iso file is fine ? easiest way is to see if the file size is as seen on the original iso... if it's not, then you might use md5 or you should download it again from the beginning if md5 is not supported.

or try, sudo apt-get update and sudo apt-get upgrade or use the auto update gui. it might help you to update and correct your system (as written on the auto update gui :D ).

or see on synaptic > custom > broken, in case you have a broken installation on your system.

:D hope this can help you....

---

