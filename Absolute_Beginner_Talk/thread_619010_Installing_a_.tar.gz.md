---
title: "Installing a .tar.gz"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Lowesifu on 2007-11-21
How do i install the tar.gz file i downloaded for flashplayer in ubuntu 7.04?

---

### Post by banewman on 2007-11-21
You need to open a terminal then change directories to where you downloaded the file to - 
you would type for example -    cd /home/desktop   - if you downloaded the tar to the desktop. Then type - 
tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo ./flashplayer-installer
and that should have it installed. :)

---

### Post by Lowesifu on 2007-11-21
ERROR: Your architecture, \'ppc\', is not supported by the
       Adobe Flash Player installer.
  

I guess that it's not meant to be.  Anyone know of any tricky ways to get Flash working on a Power PC based computer?

---

### Post by banewman on 2007-11-21
If you just need it in firefox you can use their plugin.
In bookmarks there is a firefox listing under ubuntu & free software that has "customize firefox" - go there - choose plugins - then "adobe flash".
Hope that helps :)

---

### Post by mdpalow on 2007-11-21
sudo aptitude update
sudo aptitude install flashplugin-nonfree

---

### Post by Lowesifu on 2007-11-21
> **mdpalow said:**
> sudo aptitude update
sudo aptitude install flashplugin-nonfree

i ran these two lines in my terminal then restarted firefox but still no flash. this is what it did:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by Perfect Storm on 2007-11-21
[http://www.medibuntu.org/](http://www.medibuntu.org/) is needed.

---

