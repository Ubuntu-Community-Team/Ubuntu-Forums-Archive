---
title: "Installing Updates"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by yogibearau on 2007-09-01
Im a newbie to Linux and when i try to run Synaptic package manager i get this error message (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.)

And then if I try and use Adept Manager instead i get this message (you will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.)

Can some one help as I need to install Java and a few other plug ins so I can use some applications and some Chat channels 

Regards
Mick

---

### Post by ryana on 2007-09-01
> **yogibearau said:**
> Im a newbie to Linux and when i try to run Synaptic package manager i get this error message (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.)

Regards
Mick

--------------------
Hey! I am new to linux/ubuntu, but I had a similar problem with a different application... What I did was just type what it says into the 'terminal'. So just open terminal and type 'dpkg --configure -a' and that should fix the problem, it did for me anyway :D Best of luck.

---

### Post by diatribe on 2007-09-01
run dpkg --configure -a

---

### Post by yogibearau on 2007-09-01
Hey thanks for that but when i run that i get this answer back (dpkg: requested operation requires superuser privilege)

---

### Post by Tyke91 on 2007-09-01
sudo is the superuser

so type in

sudo dpkg --configure -a

then type your username password when you're prompted (dont worry, you wont see it)

---

### Post by diatribe on 2007-09-01
> **Tyke91 said:**
> sudo is the superuser

so type in

sudo dpkg --configure -a

then type your username password when you're prompted (dont worry, you wont see it)

hehe yes my bad kindof drunk ;p

---

### Post by yogibearau on 2007-09-01
Thanks Heaps it worked now its telling me (Installing the software the marked changers are being applied this can take some time please wait) so far its taken 30 mins how long should it take ?????

---

### Post by diatribe on 2007-09-01
however long it takes, it depends on the amount of updates, then your connection speed to download and cpu speed to install

---

### Post by yogibearau on 2007-09-01
Just seems to be locked to me as the hard drive light isn't doing anything and the progress bar hasn't moved at all

---

