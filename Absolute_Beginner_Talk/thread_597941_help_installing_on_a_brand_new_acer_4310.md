---
title: "help installing on a brand new acer 4310"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by korei_ykcul on 2007-10-30
first of all it came with no OS. and xp won't work because of the SATA driver issue so i decided to go to fresh install in ubuntu. evertime i start to install booting from cd, my computer just stops. i tried to do these: 
1. acpi=off - Press F6
2. noapic
3. noapic nolapic/acpi=off
4. pci=conf1
5. live noapic nolapic - Hit ESC @ initial boots.

and i am fronted with initframs and i don't know what to do next. please help im a total noob. i wish to learn from all of you. thanks god bless

---

### Post by overdrank on 2007-10-30
> **korei_ykcul said:**
> first of all it came with no OS. and xp won't work because of the SATA driver issue so i decided to go to fresh install in ubuntu. evertime i start to install booting from cd, my computer just stops. i tried to do these: 
1. acpi=off - Press F6
2. noapic
3. noapic nolapic/acpi=off
4. pci=conf1
5. live noapic nolapic - Hit ESC @ initial boots.

and i am fronted with initframs and i don't know what to do next. please help im a total noob. i wish to learn from all of you. thanks god bless

Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the --, then press enter. When you receive the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot.

---

### Post by korei_ykcul on 2007-10-30
***glibc detected*** depmod: realloc(): invalid next size: 0x08069bc8*** abosted
spawning shell with initframs

what else to do?? tnx for helping :confused::(

---

### Post by korei_ykcul on 2007-10-30
also when i type modprobe piix: 

it says:

FATAL: could not load /lib/modules/2.622-14-generic/modules.dep: no such file or directory

it also says double free or corruption

0---------

Begin: Mounting root file system......
udevd-event 2155:run_program /sbin/modprobe abnormal exit

---

### Post by overdrank on 2007-10-30
> **korei_ykcul said:**
> ***glibc detected*** depmod: realloc(): invalid next size: 0x08069bc8*** abosted
spawning shell with initframs

what else to do?? tnx for helping :confused::(

Ok which version of ubuntu are you using 7.10 Gutsy, 7.04 Feisty? Also have you checked the cd for errors and if you have access to a system to run a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by korei_ykcul on 2007-10-30
i've just downloaded the iso from ubuntu.com ,i think its ubuntu-7.10-desktop-i386 thanks

and yes i've checked if it is 100% working and it is.

but what's wrong? why is it not installing on my acer aspire 4310?

---

### Post by korei_ykcul on 2007-10-30
everytime i type "modprobe piix" it says: FATAL: could not load /lib/modules/2.6/22-14-generic/modules.dep: No such file or directory

---

### Post by overdrank on 2007-10-31
> **korei_ykcul said:**
> everytime i type "modprobe piix" it says: FATAL: could not load /lib/modules/2.6/22-14-generic/modules.dep: No such file or directory

Hi and I believe I have seen the error before and that is why I suggested to check the MD5SUM. If it was my system I would do the steps again that you mentioned in your first post and keep track of each error and maybe that will help narrow down the issue. Sorry I could not be of more help. Good luck!

---

### Post by korei_ykcul on 2007-10-31
yes ive done an md5sum and its correct, i really won't work. so i downloaded the amd 64 edition. unfortunately for the amd64 edition the md5sum failed, so i have to download it again. anyway why is dis happening? can downloading be corrupted during process? thanks for your time

---

