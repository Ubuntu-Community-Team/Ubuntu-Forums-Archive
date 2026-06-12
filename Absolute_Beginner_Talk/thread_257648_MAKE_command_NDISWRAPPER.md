---
title: "MAKE command: NDISWRAPPER"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Drate on 2006-09-14
Basically, I am wondering why the make command is not being recognized by my Ubuntu. I am new to Linux but not to computers, and am trying to make my linksys wireless NIC work in Ubuntu via Ndiswrapper.  So if anyone could help, give it to me like I am a born again computer user.

---

### Post by Sef on 2006-09-14
To compile, build-essential needs to be installed.

Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install build-essential

---

### Post by Drate on 2006-09-16
Okay, i've gotten as far as the  "sudo apt-get install dh-make fakeroot gcc-3.4 build-essential" command but it gives me some error message about the package not being there but is referrenced by some other package and might be obsolete, etc., etc..

I tried to go on with the steps anyway, and It gives me an error message about not having this gcc3.4 dealie.  Tengo un dolor de cabeza.  Help.

BTW, I am currently running 5.10 and have no internet connection except by somebody elses machine.

---

### Post by Drate on 2006-09-18
Um, pretty please?

---

### Post by Drate on 2006-09-20
So silence, that's like a no right?

---

### Post by sailor2001 on 2006-09-20
ndiswrapper is in your synaptics........

---

### Post by aysiu on 2006-09-20
Do this: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

