---
title: "[SOLVED] Noob Alert!"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by tmofarns on 2008-04-16
so i was checking out some stuff and i found this on you tube [http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)
so i guess what i am ttrying to say is how do i know if i have copmiz and if i dont have it how do i get it and how do i Make it do that!
(on a foot note the first few minutes of the vid is windows vista youll know when it ubuntu)

---

### Post by celticbhoy on 2008-04-16
First of list your Ubuntu version, and your hardware.

---

### Post by tmofarns on 2008-04-16
ubuntu release 7.10 (gutsy)
kernel linux 2.6.22-24-generic
gnome2.20.1
amd athlon xp 2600+
440.8 mb mem
56 gb storage

---

### Post by Saint Angeles on 2008-04-16
whats your video card?

when you type: glxinfo | grep direct ... what do you get?

PS heres a screenshot from me

---

### Post by celticbhoy on 2008-04-16
Need your graphics card make and model to make sure your drivers are set up right.

But you can try and go to  --> System
                                          -->  Preferances
                                          --> Appearance
                                          Visualk Effects tab and post the setting

---

### Post by tmofarns on 2008-04-16
tra***@tra***-desktop:~$ glxinfo | grep direct
direct rendering: Yes
travis@travis-desktop:~$

---

### Post by ad_267 on 2008-04-16
Go to System - Preferences - Appearance - Visual Effects and if you have desktop effects to anything other than None then you're using Compiz Fusion. To get the other effects you have to enable them by installing compizconfig-settings-manager using synaptic or apt-get and then if you go to System - Preferences - Appearance - Visual Effects again there will be an option "Custom" where you can change all your preferences and enable other effects.

---

### Post by Saint Angeles on 2008-04-16
press alt+ f2 and type in: compiz --replace

---

### Post by tmofarns on 2008-04-16
setting is on extra

---

### Post by tmofarns on 2008-04-16
> **Saint Angeles said:**
> press alt+ f2 and type in: compiz --replace

made my screen shake and then go blank for a few seconds is that bad??

---

### Post by celticbhoy on 2008-04-16
As mentioned set to custom.
Run Synaptic package manager and search for and install compiz settings manager
then from then custom selection you will be able to set up compiz as you like.

---

### Post by sisco311 on 2008-04-16
You have compiz installed. You can install compizconfig-settings-manager(configuration tool for compiz)
```
sudo aptitude install compizconfig-settings-manager
```[or click here to install]("apt:compizconfig-settings-manager")

---

### Post by Saint Angeles on 2008-04-16
> **tmofarns said:**
> made my screen shake and then go blank for a few seconds is that bad??
naw... you are prolly running compiz right now

to test... type compiz --replace into a terminal and post the output

---

