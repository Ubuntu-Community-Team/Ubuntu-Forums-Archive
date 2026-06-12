---
title: "A sticky situation"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by iwannabealinuxuser on 2008-04-09
Hey yall,

I'm back with more newbie problems.  I recently installed Feisty Fawn on my desktop because I don't like how buggy the beta is, so I'd figure that I would install it and just upgrade to 7.10 like I did on my laptop.  Anyway as soon as it installed i ran update manager, it popped up with 200 updates needed so i began and it took like 2 1/2 hours to download about (15 failed) I figured this was due because I was missing some necessary software like on my ipod touch.  So I rebooted annnnnd now, Ubuntu stopped using my wireless card and will not auto detect it at all.  So I figured I'd download madwifi in my windows partition and run it in linux.  I got it in .tar format and thought i knew what to do, silly me, every time I try to just type make command in the madwifi directory it say something like "can't cd to /lib modules.2.6.20=16-generic/build is missing, please set KERNELPATH. Stop."  Anyway most of you would say well just hardwire it into your router well... I can't do that physically at the moment so I'm hoping you guys may have the cure for the common newbie messup

---

### Post by Crafty Kisses on 2008-04-09
You might want to post the following output:
```
iwconfig
```
Did the Wireless work before you did this?

---

### Post by iwannabealinuxuser on 2008-04-09
yeah my wireless was working before i installed those updates, anyway i tried your iwconfig command although no clue how i was supposed to use it, and got

lo   no wireless extensions.

eth0  now wireless extensions.

---

### Post by buried on 2008-04-09
```
sudo apt-get install ndiswrapper
```
and that should fix your wi-fi probs.

---

### Post by iwannabealinuxuser on 2008-04-09
my computer's response to that was

reading package lists... Done
Building Dependency Tree
Reading State Information... Done
E: Couldn't find package ndiswrapper

remember people yo tengo no internet-o

---

### Post by wannadumpwindows on 2008-04-09
It sounds like you might need to do a

```
sudo apt-get install build-essential
```

---

### Post by buried on 2008-04-09
lol sorry forgot you don't have internet, now that's really sticky, try ADSL, and installing Wi-fi it's your only choice, other then Windows

---

### Post by iwannabealinuxuser on 2008-04-09
what is adsl and where can i get it? I googled and not sure if im getting the right thing

---

### Post by Crafty Kisses on 2008-04-10
You'd have to know what driver you needed, and what Wireless card in order to run the NDISwrapper.

---

### Post by iwannabealinuxuser on 2008-04-10
oh yeah I forgot its a NETGEAR WG311T

---

