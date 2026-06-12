---
title: "Nvidia 7600GS Drivers"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-08-13
I am new in kubuntu , i have download nvidia 100.14.11 drivers and i dont know how to install them , somebody plz write how to install these drivers.

---

### Post by Spr0k3t on 2007-08-13
The 7600GS should work with the restricted drivers manager.  Try pulling the nvidia-glx-new down from the repos using: ```
kdesu apt-get install nvidia-glx-new
```

---

### Post by tseliot on 2007-08-13
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by Spr0k3t on 2007-08-13
The methods tseliot links to will work as well, but as a new user to Ubuntu, you may want to stick with what works best or easiest for you.  Taken from one of the pages linked from Feisty: > Every time you change or upgrade your kernel you will have to reinstall the Nvidia driver, no matter which method you used to install the driver.  Using the restricted-drivers-manager, you will not need to worry about reinstalling the video drivers.  I used to use the methods described by tseliot, but I became frustrated and moved on to the method introduced in Feisty.  Now every time the kernel is updated, I receive an already prebuilt package for the nvidia driver.

---

### Post by damansandhu on 2007-08-13
ok i am following method 1, now i have this problem 

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
daman@Ultimate:~$ sudo apt-get install nvidia-glx-new
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.20-16-generic: Depends: linux-image-2.6.20-16-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

