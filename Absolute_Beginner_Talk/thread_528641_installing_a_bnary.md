---
title: "installing a bnary"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by bellzii on 2007-08-18
how can i install a binary file

thanks in advance

---

### Post by nitro_n2o on 2007-08-18
A binary file(s) means that it's already been compiled and ready to run.. 
what r u trying to do?? what is the thing you want to install?

---

### Post by Nebby on 2007-08-18
It depends what kind of binary it is. If it's a .deb, you can just click on it. If it's a .rpm, you need to use alien. If its a .exe, you need a windows emulator/compatibility layer.

---

### Post by bellzii on 2007-08-18
I want to install real player , i downloaded a .bin and i want to install it

cheers

---

### Post by bellzii on 2007-08-18
what command should i use to install the .bin or binary file

---

### Post by kwacka on 2007-08-18
To install realplayer add medibuntu to your apt sources list - see [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

then 'sudo apt-get update' followed by 'sudo apt-get install realplay'

But if you really want to install it from a .bin change the permissions to make it executable Iif its not already) open a terminal, cd to directory, the chmod 755 filename.bin then run it with ./filename.bin

---

