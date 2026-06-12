---
title: "belkin wireless card"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Penumbra on 2007-04-23
my computer can boot into windows or ubuntu which is how im able to post, but i cant get my ubuntu to install my wireless card
Belkin
V1799 D7000
BCM4306/BCM2050
[http://ubuntuforums.org/archive/index.php/t-250889.html](http://ubuntuforums.org/archive/index.php/t-250889.html)
is the only post i have found of it, but i dont exactly understand how he got to the starting point
i have the CD, but i dont know how to get the drivers off of it and onto the Hard drive to be used in ubuntu

---

### Post by digital_sabotage on 2007-04-23
...here's how i think i installed and used ndiswrapper ...easy way i thought

..start synaptic package manager ...search for "ndis" ...install the latest version of ndiswrapper ...should be "ndiswrapper-utils-1.8" ...that will also install the dependency "ndiswrapper-common" automatically.
...next install "ndisgtk"   ...that's the graphical front-end for ndiswrapper ...after that is installed you should be able to go to >System>Administration>Windows wireless drivers  ...a window will open allowing you to install a driver ...navigate to where your .inf file is and you should be good to go

...after that you should see your wireless card in >System>Administration>Networking ...you will need to specify the ssid and wep password there ...just type "any" beside ssid if you want to use un-encrypted signals (coffee shop etc.)  ...then make sure wireless check boxes are "enabled"  ...should configure and connect ...hope this helps  ...good luck:-)

---

