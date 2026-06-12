---
title: "X Windows not installed by default..."
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by frostoftheblack on 2005-09-14
Hello, very new to Ubuntu here. Just installed today and I had some major installation issues as I had to reinstall many times because installation failed. (This isn't unique to Linux, there is something wrong with the motherboard which needs to be fixed which also happens in Windows). Anyway, I was able to successfully complete an install, but GNOME and XWindows do not seem to be installed because when I login, I only get the console, no GUI. I've tried running aptitude but I can't seem to install new packages. Any ideas would be much appreciated.

Frost

---

### Post by mlomker on 2005-09-14
The command to start the graphical environment is **startx**.

I don't use aptitude, but you didn't explain the error you were getting anyway.

Try:

```

apt-get update
apt-get upgrade

```

---

### Post by codejunkie on 2005-09-14
[QUOTE=frostoftheblack]Hello, very new to Ubuntu here. Just installed today and I had some major installation issues as I had to reinstall many times because installation failed. (This isn't unique to Linux, there is something wrong with the motherboard which needs to be fixed which also happens in Windows). Anyway, I was able to successfully complete an install, but GNOME and XWindows do not seem to be installed because when I login, I only get the console, no GUI. I've tried running aptitude but I can't seem to install new packages. Any ideas would be much appreciated.

Frost[/QUOTE]
this will happen if you do a server install it dosent install a gui interface by default or if the cd you used to installed from was damaged run this in the terminal and it will install Xwindows and gnome ```
sudo apt-get install ubuntu-desktop
```

---

### Post by heimo on 2005-09-14
Here is a way to test that X Window system and related graphical user interface packages were installed properly.
 ```
sudo apt-get install ubuntu-desktop
``` 

If it doesn't want to install anything, X Window system, Gnome and all relevant is there already, but not running for some reason. You can try to start login manager (graphical logon screen) with:
 ```
sudo /etc/init.d/gdm start
``` 
Sometimes it helps to stop it first and then start. Does it do anything? Any errors? If so, you can try to reconfigure Xorg server, which is the X Window system on Ubuntu:
 ```
sudo dpkg-reconfigure xserver-xorg
``` 
This will ask many questions about keyboard, mouse, monitor and graphics card.

If you didn't have all the ubuntu-desktop packages installed and have some kind of partial install - some packages not configured properly, some packages missing or anything like that, you should try something like this;
 ```

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get upgrade (this will upgrade all packages)

``` 


Post back what you found out and we'll be glad to help you solve this problem if possible. :) Welcome to Ubuntu!

---

### Post by frostoftheblack on 2005-09-14
[QUOTE=codejunkie]this will happen if you do a server install it dosent install a gui interface by default or if the cd you used to installed from was damaged run this in the terminal and it will install Xwindows and gnome ```
sudo apt-get install ubuntu-desktop
```[/QUOTE]

That's what I did, just the base install because I was having problems installing the default. I'll try it again.

Thanks a lot for the help both of you.

---

