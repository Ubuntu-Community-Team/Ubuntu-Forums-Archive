---
title: "compiz problem"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by scottc992004 on 2008-03-22
ok when i go to enable visual effects in Appearance preferences. i get "The composite extensionis not available". Why does this appear. How can i fix this?

some info from terminal:

mdk@mdk:~$ dpkg -l | grep compiz-core
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1        
OpenGL window and compositing manager

mdk@mdk:~$ dpkg -l | grep compizconfig-settings-manager
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1          
Compiz configuration settings manager

mdk@mdk:~$ glxinfo | grep -i direct
direct rendering: Yes
mdk@mdk:~$

---

### Post by herbster on 2008-03-23
Which video card are you using and paste the output of:

```
compiz --replace
```

Hitting CTRL+C to cancel it once you get output, should it not terminate due to error.

---

### Post by scottc992004 on 2008-03-23
my graphics card is ATI RADEON X2300

mdk@mdk:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Oldsoldier2003 on 2008-03-23
> **scottc992004 said:**
> my graphics card is ATI RADEON X2300

mdk@mdk:~$ compiz --replace
Checking for Xgl: not present. 
[COLOR="Red"]No whitelisted driver found
aborting and using fallback: /usr/bin/metacity[/COLOR]

thats why. you dont have a driver that supports compiz, have you installed the restricted drivers?

If you have and your drivers are blacklisted, then you might take a shot at using envy to try to get around it.

---

### Post by scottc992004 on 2008-03-23
can i use another like compiz or will i still have the same problem and how do i get envy.

---

### Post by PreviousN on 2008-03-23
Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It's pretty automatic. Be sure to have it rewrite your xorg when it's done. I think it automatically makes a backup, but you may wish to back up yourself.

---

### Post by scottc992004 on 2008-03-23
what do i back up and where is it?

---

### Post by Ub1476 on 2008-03-23
The "composite extension is not available" error, means that XGL is not installed. If you have the error with the current drivers install it:

```
sudo apt-get install xserver-xgl
```

If you plan on installing Envy, remove the driver from Restricted Driver Manager first, then launch Envy, and let it install and configure X (xorg.conf) for you. 

You do not need XGL if you want to use Envy.

It's not required to backup your xorg.conf either (if you remove all previous drivers and then let Envy install the new one).

---

### Post by scottc992004 on 2008-03-23
installed it. but still get The "composite extension is not available" error

---

