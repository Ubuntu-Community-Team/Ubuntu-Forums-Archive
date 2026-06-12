---
title: "Trouble instally ATI driver from ATI.com"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-05-02
Please see attachment. The screenshot shows an error. Does anyone know what the error is and how to resolve it? The .run file is highlighted.
Thanks for any and all help.
kh

---

### Post by starcraft.man on 2007-05-02
Try [Envy...]("http://www.albertomilone.com/nvidia_scripts1.html") ATI has a bit more trouble working on Ubuntu in my experience. 

Download and install the 0.9.2 Debian by double clicking it. Then go to Applications > System Tools > Envy. That should open a gui, select automatically install ati drivers and let it run, answer yes to any prompts and when you reboot it should be working like a charm.

Hope that helps.

---

### Post by kittyhawk63 on 2007-05-02
> **starcraft.man said:**
> Try [Envy...]("http://www.albertomilone.com/nvidia_scripts1.html") ATI has a bit more trouble working on Ubuntu in my experience. 
Download and install the 0.9.2 Debian by double clicking it. Then go to Applications > System Tools > Envy. That should open a gui, select automatically install ati drivers and let it run, answer yes to any prompts and when you reboot it should be working like a charm.
Hope that helps.
Thanks.
kh

---

### Post by lamalex on 2007-05-02
why not just use the restricted drivers manager? you're using feisty based on your mini-bio over there..

---

### Post by starcraft.man on 2007-05-02
> **Iamalex said:**
> why not just use the restricted drivers manager? you're using feisty based on your mini-bio over there..

I dunno, I've heard a few people that had trouble with it, and it leaves out the settings manager which envy puts in and I think is important, people should be able to tweak settings. Maybe I'm just picky and like envy :p

---

### Post by kittyhawk63 on 2007-05-02
> **Iamalex said:**
> why not just use the restricted drivers manager? you're using feisty based on your mini-bio over there..

I've tried opening that. It says: Your hardware does not need any restricted drivers.

I had Beryl working but it was very slow and jumpy. I was trying to install the ATI drivers from ATI.com. I thought they would work better. Maybe fglrx is the way I need to go. I had the default drivers only. Any suggestions? I am using an ATI Radeon 9200 SE video card.
kh

---

### Post by starcraft.man on 2007-05-02
Ummm, did the envy ati driver install work?

---

### Post by lamalex on 2007-05-02
try ```
sudo ]apt-get install linux-restricted-modules-`uname -r`
``` and then try restricted modules, if it doesn't you can get the driver manually by ```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by kittyhawk63 on 2007-05-02
> **Iamalex said:**
> try ```
sudo ]apt-get install linux-restricted-modules-`uname -r`
``` and then try restricted modules, if it doesn't you can get the driver manually by ```
sudo apt-get install xorg-driver-fglrx
```


kittyhawk63@kittyhawk63:~$ sudo apt-get install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.20-15-generic is already the newest version.
linux-restricted-modules-2.6.20-15-generic set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kittyhawk63@kittyhawk63:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-05-02
> **starcraft.man said:**
> Ummm, did the envy ati driver install work?

no. Couldn't get Envy to install.

---

