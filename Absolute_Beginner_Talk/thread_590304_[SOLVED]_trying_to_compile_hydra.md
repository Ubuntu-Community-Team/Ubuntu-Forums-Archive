---
title: "[SOLVED] trying to compile hydra"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-10-24
HOW!!! im stuck everytime i run it in terminal it wont work, says i need to compile from source?

---

### Post by Crafty Kisses on 2007-10-24
First you should try the following command:
```
cd /home/$/Hydra
```
The dollar sign should represent your directory, after that it should say 
```
Hydra$
```
Then type the following:
```
./configure
```
Then after that type:
```
make install
```
Then it should be compiled.

---

### Post by LiNuXxToOthEMaX on 2007-10-24
> **Codename said:**
> First you should try the following command:
```
cd /home/$/Hydra
```
The dollar sign should represent your directory, after that it should say 
```
Hydra$
```
Then type the following:
```
./configure
```
Then after that type:
```
make install
```
Then it should be compiled.

after i did that i get the following error:
```
Did not find cross-compiler
```

---

### Post by Maestro23 on 2007-10-24
If you don't have build-essential installed, you need it first.

> sudo apt-get install build-essential

*And if there is a README/INSTALL doc with the program, read it.

---

### Post by Crafty Kisses on 2007-10-24
> **LiNuXxToOthEMaX said:**
> after i did that i get the following error:
```
Did not find cross-compiler
```

That actually sounds like your trying to install "The Palm" version of Hydra, try to install the full version, you probably typed the following command:
```
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly
```
That's what it tells you to type after you type "Make Install" but after you type "Make Install" just type the following:
```
make
```
Then it should work, tell me.

---

### Post by Crafty Kisses on 2007-10-24
That build-essentials would help too, haha.

---

### Post by LiNuXxToOthEMaX on 2007-10-24
> **Codename said:**
> That actually sounds like your trying to install "The Palm" version of Hydra, try to install the full version, you probably typed the following command:
```
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly
```
That's what it tells you to type after you type "Make Install" but after you type "Make Install" just type the following:
```
make
```
Then it should work, tell me.

thanks codename that worked haha, ya i was typing the command for the palm version it was telling me to haha, it compiled thanks codename!!! thanks everyone

---

### Post by Crafty Kisses on 2007-10-24
> **LiNuXxToOthEMaX said:**
> thanks codename that worked haha, ya i was typing the command for the palm version it was telling me to haha, it compiled thanks codename!!! thanks everyone

No problem man. :)

---

### Post by Maestro23 on 2007-10-24
Good deal man.  Please mark this SOLVED using the Thread Tools.

Thanks. :)

---

### Post by Crafty Kisses on 2007-10-24
> **Maestro23 said:**
> Good deal man.  Please mark this SOLVED using the Thread Tools.

Thanks. :)

Now, only if every Linux problem was that easy to solve. ;)

---

