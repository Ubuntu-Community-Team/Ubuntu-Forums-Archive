---
title: "Having a REAL hard time so far :("
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by chesman on 2006-12-31
So i have Ubuntu installed, and i am getting overly frustrated with the graphics driver.

Whenever i browse websites, or anything that i have to scroll, it is VERY laggy and choppy, i have tried installing the ATI card from their website for my X1300, but still did not fix it, i have also tried the steps in the forums, and even tried useing Easy Ubuntu, but i get an error when i try to install the ati driver through that. It picks up the repository that was given in the testing ATI/NV drivers thread, and downloads it, but i get this error every time :(

> E: /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.30.3+2.6.17.9-1_i386.deb: trying to overwrite `/usr/sbin/atieventsd', which is also in package fglrx-6-8-0
E: /var/cache/apt/archives/fglrx-control_8.30.3+2.6.17.9-1_i386.deb: trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-6-8-0

Would reinstalling ubuntu fix this? and try installing the drivers again?

please help with my frustration :)

Thank you

---

### Post by riven0 on 2006-12-31
Chesman, have you tried [this howto]("http://www.ubuntuforums.org/showthread.php?t=190133&highlight=installing+ati+drivers")? It may help.

---

### Post by Sammi on 2006-12-31
You seem to not be able to install, so your problem seems to be related to Apt, which is the program that you install everything with in Ubuntu, not the driver itself.

---

### Post by Hendrixski on 2006-12-31
could be a problem of insufficient priviledges, are you sure you're doing this as root?

I suspect you may be missing packages from your /etc/apt/sources.list file.  By default a lot of them are commented out, or you may need to get new ones. open that file with a text editor of your choice and make sure none of the lines with the "deb http://,,,,,,," are commented out (that is, that they have a "#" in frontof them.  :)

---

### Post by Sammi on 2006-12-31
Here are a few guides to enabling extra repositories:

Edgy Eft:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software)

Dapper Drake:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories)

Breezy Badger:
[http://ubuntuguide.org/wiki/Ubuntu#Repositories](http://ubuntuguide.org/wiki/Ubuntu#Repositories)

Anyway, when I study you error output again it seems that Apt wont't let the new driver overwrite the old driver files. Uninstalling the old driver first might solve this problem.

---

