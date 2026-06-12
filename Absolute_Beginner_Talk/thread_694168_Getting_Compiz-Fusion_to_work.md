---
title: "Getting Compiz-Fusion to work"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by AlexLinuxUser101 on 2008-02-11
Hey I just installed Ubuntu, and when I did it told me to install some updates (including compiz fusion).  It said that it installed it, but it doesn't work (I only have 2 desktops and no "cube" for example).  Can anyone give any suggestions?  Thanks!

---

### Post by jan quark on 2008-02-11
what is your video card?

do you have installed the drivers for it?

do you have tried to set the effects on with appearance settings ?

---

### Post by jordanmthomas on 2008-02-11
Provided compiz is working, but you just have no cube:
You need to install compizconfig-settings-manager
The easiest way (I think) to install it is to open a terminal and type
```
sudo apt-get install compizconfig-settings-manager
```

Then, you can go to system -- preferences -- appearance and the desktop effects tab and go to custom to enable the cube among other things.

---

### Post by AlexLinuxUser101 on 2008-02-11
This is pretty noobish, but when I do that I get 
alastname@Alex-Computer:~$ sudo apt-get install compizconfig-settings-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Joeb454 on 2008-02-11
Search Add/Remove for Compiz, and install the Advanced Settings Manager.

Then under the General tab you should be able to set the Desktop size. It just needs increasing to 4 :) That's why you have no Cube...so Compiz is actually working, just not how you want it to yet :)

---

### Post by jordanmthomas on 2008-02-11
> **AlexLinuxUser101 said:**
> This is pretty noobish, but when I do that I get 
alastname@Alex-Computer:~$ sudo apt-get install compizconfig-settings-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This means some other program that handles packages is running.  It could be the update manger, you may have Synaptic or Add/Remove Programs open, etc.

---

### Post by shafin on 2008-02-11
Also,on the custom tab,go to preferences and select flat file backend instead of the gconf backend.

---

### Post by jordanmthomas on 2008-02-11
> **shafin said:**
> Also,on the custom tab,go to preferences and select flat file backend instead of the gconf backend.

Mind if I ask why?  I am sure there's a good reason, but I don't know why you wouldn't want to use gconf.  Is it so you can back your settings up easier?

---

### Post by AlexLinuxUser101 on 2008-02-11
Hey everybody thanks a ton for all the help, I got it.  This community is so helpful and awesome.  Thanks

---

### Post by Joeb454 on 2008-02-11
No Problem :) Don't hesitate to post more if you need help with anything :)

---

