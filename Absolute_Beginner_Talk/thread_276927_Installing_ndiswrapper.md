---
title: "Installing ndiswrapper"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by unrealmstr on 2006-10-13
When I try to install ndiswrapper 1.25, i change to its folders directory and type make, but i get this:
```
root@unrealmstr:~/Desktop/ndiswrapper-1.25# make
make -C driver
make[1]: Entering directory `/root/Desktop/ndiswrapper-1.25/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/root/Desktop/ndiswrapper-1.25/driver'
make: *** [all] Error 2

```
it says it needs the path to the kernel build directory :confused: 
all help is appreciated :-D

---

### Post by petri on 2006-10-13
I thought ndiswrapper is in repos and can be installed with Synaptic but I could be wrong.

---

### Post by unrealmstr on 2006-10-13
is it installable from the ububntu cd? otherwise i have to do it manually because i dont have the interwebs (thats why im installing ndiswrapper)

---

### Post by agc on 2006-10-13
Can you plug your computer into an ethernet connection?
If you can, then you can install ndiswrapper from
adept / synaptic / apt-get (whatever is easier for you).

---

### Post by unrealmstr on 2006-10-13
I can but i dont want to have to lug my tower allthe way downstairs to my router:(

---

### Post by agc on 2006-10-13
The pain of carrying your 'tower' ( = computer?) downstairs may
be far less than trying other ways to solve this problem :)

---

### Post by unrealmstr on 2006-10-13
yes computer, sorry about that, i guess ill do that then thanks for your help :)

---

### Post by petri on 2006-10-13
In my DesktopCD 6.06 I do find ndiswrapper :-D  the path is /media/cdrom0/pool/main/n/ndiswrapper

EDIT: and then just doubleclick the *.deb

---

### Post by unrealmstr on 2006-10-13
thankyou for the help everyone ndiswrapper is installed :D

---

### Post by Haiyadragon on 2006-10-21
Note to devs: It might be a fairly good idea to install ndiswrapper and all other wireless drivers by default. It's not 1985 anymore. Also, full support (as in graphical) for all encryption types upto wpa2-psk.

This kinda annoys me since I just installed Ubuntu on one of my computers only connected through wireless. Was expecting better wireless support. Connecting it directly shouldn't be required.

---

### Post by goatmale on 2006-10-21
[http://www.nubuntu.org/](http://www.nubuntu.org/)
Nubuntu comes with network ubuntu.

---

