---
title: "Booting based on Boot Device Priority?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by trunks14 on 2007-05-26
i've installed Windows and Ubuntu in two diferent Disks, but my current situation is lame :(, i have to change the IDE cable in roder to swtich from windows to ubuntu :(, ok seriously, if i plug them like master/slave (Windows Master), will the two disks prevent each other from booting? or does the system takes read MBR based on the Boot device priority?

I'd really like not to use GRUB and instead, change the boot device priority depending on the SO i want to use, however i'm too scared to try it myself (lol, i once put a HardDrive as Pri Master and a CD-ROM as Pri Slave [XD] and it screwed the partition), besides, i don't have much background on booting etc.

---

### Post by Happy_Man on 2007-05-26
Why don't you want to use GRUB?

---

### Post by Nekiruhs on 2007-05-26
You need GRUB to start Ubuntu, the windows bootloader is a PAIN to configure.

---

### Post by trunks14 on 2007-05-28
U_U it's not that i dont want to use GRUB, i dont want to have it load windows, as this computer is used by many users i don't want them to complain about that black and ugly screen asking them to cxhoose a OS.

---

### Post by bone43 on 2007-05-28
> **trunks14 said:**
> U_U it's not that i dont want to use GRUB, i dont want to have it load windows, as this computer is used by many users i don't want them to complain about that black and ugly screen asking them to cxhoose a OS.

Well you could change your boot order in grud to load windows so there is not input needed from users, then reduce the boot choice screen time to say 5 seconds or even less and they really just have to wait a few exstra seconds for windows to load.

---

