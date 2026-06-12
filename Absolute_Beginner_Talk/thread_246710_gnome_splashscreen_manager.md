---
title: "gnome splashscreen manager"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Copps on 2006-08-29
i've finished my first ubuntu install this evening and am now trying to customise the look of it - not too keen on the default brown theme!

anyhow, i'm doing ok but having a problem when trying to install a new splash screen. reading [http://doc.gwos.org/index.php/UbuntuBlue](http://doc.gwos.org/index.php/UbuntuBlue) it says to install splashscreen manager, but apt-get cannot find the package:

xand@PC1:~$ sudo apt-get install gnome-splashscreen-manager
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnome-splashscreen-manager

is there an alternate/newer package i can use for this?

thanks in advance

---

### Post by PPAAUULL on 2006-08-29
You might want to take a look at this page. It helped me do a lot of customization on my desktop. [http://www.freesoftwaremagazine.com/articles/change_ubuntu_look?page=0%2C0](http://www.freesoftwaremagazine.com/articles/change_ubuntu_look?page=0%2C0)

Hope that helps.

Paul

---

### Post by Jagot on 2006-08-29
gnome-splashscreen-manager is in the universe repository which is not enabled by default.  See either of these methods to do so:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Copps on 2006-08-29
thanks jagot, problem solved!

---

### Post by delio on 2006-08-31
I have managed to replace the splash screen due to some info in this thread, but what I am trying to figure out is how to change the color of the screen behind it to be blue as well as it is currently the default brown and I am trying to get change it to more of a blue).

I hope I am describing it right... but basically the wallpaper that is behind the splash screen as ubuntu is loading. I have a custom wallpaper but it doesn't kick on until after this point.

Thanks in advance for the help.

---

### Post by delio on 2006-09-01
Bump!??!?!

---

### Post by jordanmthomas on 2006-09-01
Go to System --> Administration --> Login Window
It is an option on the first screen that comes up  (labeled 'background color')

---

