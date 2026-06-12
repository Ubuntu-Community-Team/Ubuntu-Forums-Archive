---
title: "X display error"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by alon_pex on 2008-02-07
hi everyone,

i need help here. i am a new user of ubuntu 7.04.
while trying to intall the driver of my video card ati radeon 9600, i edited some codes in the terminal.
then i rebooted my computer to activate the effects of my edited code.
now, its seems that an error had occured. it says X display error, no screen found.
how can i fix this problem?
how can i set the terminal to its default state?

---

### Post by talsemgeest on 2008-02-07
From the terminal type ```
 sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
This will allow you to reconfigure your xserver

---

### Post by kesman on 2008-02-07
Use a software called envy to install drivers for your ati card. Also, consider switching to ubuntu 7.10, since it handles the graphics much better.

---

### Post by jan quark on 2008-02-07
the terminal command above let's you configure the x server manually 

this method configures the x server automatically 

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by Rocket2DMn on 2008-02-07
The OP has already been taken care of :) - [http://ubuntuforums.org/showthread.php?t=690066](http://ubuntuforums.org/showthread.php?t=690066)

---

### Post by kesman on 2008-02-07
Oh how nice for him to do multiple posts. Maybe mark this thread solved now?

---

### Post by jan quark on 2008-02-07
lol great minds think alike

he rocket ? :)

---

