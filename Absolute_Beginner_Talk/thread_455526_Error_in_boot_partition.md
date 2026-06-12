---
title: "Error in /boot partition"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-05-26
Hi everyone! Im an Ubuntu user who has been struggling with GRUB since the first time i installed it, 2 years ago. My problem is that whenever i turn off my computer, numerous GRUB errors pop up randomly while grub loading stage 1.5 is loading. By random i mean ive got error 16, 17, 18, 21, 23 and today got for first time number 25. 

I followed some instructions about how to fix it, created a 128 MB partition and mounted it on /boot while installation. Everything seemed to be ok, but today when i woke up and started up the machine, i got that Error 25, that is "Disk read error" according to GRUB documentation. And then, when i rebooted in order to be able to enter grub, another error message appeared: 
"GRUB loading stage 1.5Disk read error" (no, i didnt forgot the space, the original message does not have it).

Here is my fdisk -lu, with something strange i wanna point out:

Disco /dev/hda: 40.0 GB, 40060403712 bytes
255 cabezas, 63 sectores/pista, 4870 cilindros, 78242976 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes

Disposit. Inicio     Comienzo                  Fin        Bloques       Id      Sistema
/dev/hda1                           63         257039       128488+     83     Linux
/dev/hda2                  257040      2249099          996030      82    Linux swap / Solaris
/dev/hda3               2249100     78236549     37993725     83     Linux

Look at the starting sector of hda1. Shouldn`t it start in sector 0 and not in sector 63? Is this normal or its just me?

Any ideas how to get my /boot partition work well?

Thanks, cheers

---

### Post by oilchangeguy on 2007-05-26
you've been trying to get grub to work for 2 years?????? what version of ubuntu are you running? sounds like it's time to try a newer version.

---

### Post by ferpadro on 2007-05-26
no lol, i meant this same error started when i installed hoary like 2 years ago. I have installed dapper, edgy and now i have feisty, thinking that the problem would be solved by having the up to date distro but im still stuck...

---

### Post by oilchangeguy on 2007-05-26
> **ferpadro said:**
> no lol, i meant this same error started when i installed hoary like 2 years ago. I have installed dapper, edgy and now i have feisty, thinking that the problem would be solved by having the up to date distro but im still stuck...

are you doing upgrades to the newer versions? or are you doing a clean install? the clean install is the way to go. upgrading is not going to make pre-existing problems go away.

---

### Post by ferpadro on 2007-05-26
I did a clean install, and i only have Ubuntu installed, not WinXP, just to see if it wasnt a dual boot problem but it seems not :(

---

