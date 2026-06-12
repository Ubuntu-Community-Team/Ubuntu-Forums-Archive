---
title: "Adobe Flash plug in"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Panganat on 2007-05-26
installed Adobe Flash plug in, the received a promt to delete xpti.dat file.  Problem is that i cannot find the file.  It is part of the Moziila system files.


Help Me; Ayuda me

---

### Post by starcraft.man on 2007-05-26
> **Panganat said:**
> installed Adobe Flash plug in, the received a promt to delete xpti.dat file.  Problem is that i cannot find the file.  It is part of the Moziila system files.


Help Me; Ayuda me

Uhhhh... did you follow [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox") guide for installing flash? How did you install it if not that way? I have installed flash plugin hundreds of times and never been told to delete something of mozilla/firefox.

I'd say remove flash (however you put it in) and then reinstall it with the link I gave ya, that method has never failed me to date... :)

Unless someone knows why flash would want the xpti.dat file deleted?

---

### Post by aysiu on 2007-05-26
I've also never heard of being asked to delete a file in order to install the Flash plugin.

This tutorial gives you instructions for about four different ways you can install Flash (none of which asks you to delete the xpti.dat file):
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by starcraft.man on 2007-05-26
> **aysiu said:**
> I've also never heard of being asked to delete a file in order to install the Flash plugin.


YAY! At least I know now its not some nooby thing I never heard of since you don't know it either Aysiu :D.

---

### Post by Pizarro on 2007-05-26
just tried to install flash and was also asked to delete that file. I couldn't find it either.:(    Tried   sudo aptitude update && sudo aptitude install flashplugin-nonfree    and still get told....  An update for the Flash player is required. Click here to get a recent version and then try again.

---

### Post by aysiu on 2007-05-26
Can you paste the output of these two commands? The first command may take about two minutes to execute: ```
sudo updatedb
locate xpti.dat
```

---

### Post by Pizarro on 2007-05-27
martyn@martyn-desktop:~$ sudo updatedb
Password:
martyn@martyn-desktop:~$ locate xpti.dat
/home/martyn/.mozilla/firefox/vkuuxfit.default/xpti.dat
martyn@martyn-desktop:~$ 
  Hope this helps you help me !!

---

### Post by nuktar on 2007-05-27
Add/install software... much easier.

---

### Post by Pizarro on 2007-05-27
Only easier if it works!!!!

---

### Post by aysiu on 2007-05-27
Okay. Don't know why you're being asked to remove it, but go ahead and remove it: ```
rm /home/martyn/.mozilla/firefox/vkuuxfit.default/xpti.dat
```

---

