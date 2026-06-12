---
title: "Radeon XPress 200M"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by JazzSquares on 2008-02-21
I'm new to the whole Linux thing so I hope I can give you all the information necessary. I have a Radeon XPress 200M graphics card. I have followed the instructions for installing the   xorg-driver-fglrx but when I type in sudo apt-get install xorg-driver-fglrx fglrx-control linux-restricted-modules-generic it says that the package is missing, obsolete, or is only available by another source. 

I have no idea what to do and I just got LInux about two days ago, so I"m not very good at this. Hope you can help.

---

### Post by uberlube on 2008-02-21
use envy to install driver.

---

### Post by uberlube on 2008-02-21
use envy to install driver.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by GSF1200S on 2008-02-21
> **JazzSquares said:**
> I'm new to the whole Linux thing so I hope I can give you all the information necessary. I have a Radeon XPress 200M graphics card. I have followed the instructions for installing the   xorg-driver-fglrx but when I type in sudo apt-get install xorg-driver-fglrx fglrx-control linux-restricted-modules-generic it says that the package is missing, obsolete, or is only available by another source. 

I have no idea what to do and I just got LInux about two days ago, so I"m not very good at this. Hope you can help.

First off, envy might be a good route for you. If X crashes the next time you boot up, throw in this command:

sudo dpkg-reconfigure -phigh xserver-xorg

select your resolution and the 'vesa' driver. Then type in 

sudo /etc/init.d/gdm restart

Take the above down just in case envy fails to get it right ;)

Have you checked the restricted drivers manager in System-->Administration? I have the exact same card on my second lappie and all I had to do was check the box within the manager next to the card. Worked great..

**EDIT** Make sure you enable all the repositories in Synaptic Package Manager (System-->Administration).

---

### Post by JazzSquares on 2008-02-21
Okay I'm trying Envy now. I did try to click the button in the Restricted Devices section but it didn't work.That may have been because I didn't have all the repositories functioning.

**EDIT**
I installed it with Envy. When I go to the Restricted Devices it says it's in use so hopefully it's working. Thanks.

---

### Post by GSF1200S on 2008-02-21
> **JazzSquares said:**
> Okay I'm trying Envy now. I did try to click the button in the Restricted Devices section but it didn't work.That may have been because I didn't have all the repositories functioning.

Im not to familar with Envy, but if it uses the repos to get the driver, it still wont work.

Make sure the repos are enabled :)

---

