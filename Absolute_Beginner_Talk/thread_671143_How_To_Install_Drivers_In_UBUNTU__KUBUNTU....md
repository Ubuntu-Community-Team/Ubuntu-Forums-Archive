---
title: "How To Install Drivers In UBUNTU / KUBUNTU...?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by 7mm on 2008-01-18
Hit There, I Need To Install nVIDIA Drivers In UBUNTU / KUBUNTU. My Freind Using UBUNTU & KUBUNTU For My Machine. We've Got Same Hardware In Our Machine & Just Learning How Both The OS Runs & Do Best. Since We're New To Linux, Just Unable To Install The Drivers For Graphics. Please Help !

---

### Post by kulight on 2008-01-18
use ENVY it automated the installation of the G drivers

do ENVY in google

that what did it for me

---

### Post by Christmas on 2008-01-18
You do
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
Then type ALT+CTRL+F1 to go into console mode and restart the X Server:
```
sudo /etc/init.d/kdm restart
```
(assuming you use Kubuntu)

---

### Post by balaknair on 2008-01-18
The easiest way is to use the Restricted Drivers Manager and enable restricted drivers
System menu>Administration>Restricted Drivers Manager

It will connect to the net and download--> install the drivers.

---

### Post by Sef on 2008-01-18
> The easiest way is to use the Restricted Drivers Manager and enable restricted drivers
System menu>Administration>Restricted Drivers Manager


That is for Ubuntu.   

For [Kubuntu]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"):

> KMenu &#8594; System Settings, go to the Advanced tab and click Restricted Drivers. Then click the Administrator Mode button and check the box marked Enable to install the driver. This should install the right package for your card and set it up for you.

---

### Post by 7mm on 2008-01-19
**Thank You EveryOne For Your Assistance. It's Been Done Just The Way "Sef" Guided.**

---

