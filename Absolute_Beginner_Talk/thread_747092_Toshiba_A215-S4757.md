---
title: "Toshiba A215-S4757"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by wilk3sy on 2008-04-06
Hey, I'm new to ubuntu, but through this website and a few others I have learnt quite a bit over the weekend. 

I have a Toshiba A215-S4757, and from what i've learnt and experienced, its an absolute nightmare when it comes to ubuntu.

My current problems, are the wireless card isnt recognized its the Atheros 5006GE, or EG cant remember how it ends. Ive installed the latest madwifi, and followed over 10 different tutorials to try different things, and so far have had no luck!!!! ggrrr

Aswell as the wireless problem, I have a graphics driver problem. It has an ATI x1200 onboard graphics card, to which I have installed the restrictive driver set suggested by ubuntu. This hasn't worked so i can't get the higher effect levels at the moment.

Does anyone have or has had this problem? also is there anyway to fix? or am i going to have to wait for the summer til i get a new desktop. After the "hacking competition" the other week, ive decided linux is the way forwards, as ive always wanted to convert myself and become a linux user!

Cheers!

---

### Post by mikeyphi on 2008-04-06
This from the net about your Atheros card:-

Ubuntu ships madwifi in the restricted component, which is enabled in the default install. Madwifi chipsets should therefore ‘just work’.

In case you did a manual install, try installing linux-restricted-modules-$(uname -r) and that’s it. 

See: [https://wiki.ubuntu.com/LaptopTestingTeam/AsusA8M?](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA8M?)

and:  [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by wilk3sy on 2008-04-07
hmmm... well it doesnt seem to work no matter what i do. Ive known of people to get it working, but to what extent? i was hoping to get the compiz fusion plugins, but i dont think thats goin to happen on this laptop now. 

wats peoples thoughts on there being a new set of drivers in the new version?

---

### Post by mikeyphi on 2008-04-07
> **wilk3sy said:**
> 
whats peoples thoughts on there being a new set of drivers in the new version?

Download the 8.4 Beta LiveCD and see for yourself!
[http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)

---

