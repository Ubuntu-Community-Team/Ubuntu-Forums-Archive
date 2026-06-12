---
title: "Dual boot with Centos could it be possible"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-07-11
hello all ..., 

i have feisty installed on my laptop but i want to install Centos and make adual boot cause of administration stuff could any one here tell me how to make that without any grub failure cause it failed with RHEL4 when i tried to make a dual boot

---

### Post by sab0403 on 2007-07-11
My guess is if you tell the CentOS installation (which I'm not familiar with) to NOT install GRUB, and then manually add it to the GRUB menu later?

Also you should only need one extra partition, since the swap could be used by either OS...

Is there an option to install/not install GRUB? Alternatively you could let CentOS install it, and manually add Ubuntu to it later (just check your GRUB settings now and write/print them)...

Hope this helps.

---

### Post by sab0403 on 2007-07-11
I guess I forgot to ask: have you manually edited GRUB before?

---

### Post by black_ice on 2007-07-11
thanx for you replay 

by the way i asked this question cause i suffered before from my RHEL installation i did this steps

1- i have the ubuntu installed 

2- i made a partition for the / of the new RHEL installation 

in the boot menu ubuntu was detected but when i want to enter it it gave me an error something like grub chain error 

so am afraid of repeat that on centos installation so i want to know the best way to make daul boot with ubuntu

---

### Post by sab0403 on 2007-07-11
Oh ok... something like:```
Booting Windows at hdd1
rootnoverify (hd1,0)
chain loader +1
Error 21: selected disk does not exist
Press any key..
```this?

---

### Post by sab0403 on 2007-07-11
Well, I have to go know... work and all...

Anyway, if that's the kind of message the GRUB loader gave you before, try installing it normally, then if you see any problems, search the forums for "chainloader error".

---

