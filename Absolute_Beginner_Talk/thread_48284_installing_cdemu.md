---
title: "installing cdemu"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by user on 2005-07-11
ok i already did apt-get update and got the newest gcc too.
first i extracted what's in the compressed file and, as the manual says, did 
```
/lib/modules/2.6.10-5-386/build/include
```
but i get 
```
No such file or directory
```
so i did
```
/lib/modules/2.6.10-5-386 /build/include
```
then i got 
```
bash: /lib/modules/2.6.10-5-386: is a directory
```

well, after that i did "make" and i got this messege;
```
make: *** No rule to make target `cdemu.ko', needed by `modules'.  Stop.
```, both cases.
so... what should i do?

---

### Post by tonysathre on 2005-08-10
it doesnt look like u are typing any kind of command...did u cd into the directory first

---

### Post by poofyhairguy on 2005-08-10
> **user]ok i already did apt-get update and got the newest gcc too.
first i extracted what's in the compressed file and, as the manual says, did 
```
/lib/modules/2.6.10-5-386/build/include
```
but i get 
```
No such file or directory
```
so i did
```
/lib/modules/2.6.10-5-386 /build/include
```
then i got 
```
bash: /lib/modules/2.6.10-5-386: is a directory
```

well, after that i did "make" and i got this messege said:**
> 

Did you install build essential?

[QUOTE]sudo apt-get install build-essential

---

