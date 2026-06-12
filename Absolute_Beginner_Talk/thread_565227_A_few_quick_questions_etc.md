---
title: "A few quick questions etc"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by littlestkiwi on 2007-10-02
Hey, just installed ubuntu, loving it so far, just wondering a few things. How do i increase the the resolution? its only at 1024x768 would like to get it a bit higher. Also do i need to install drivers?(would have though you would) and if so were would a good place to get them from be?

---

### Post by mindtrick on 2007-10-02
System > Preferences > Screen resolution 

You need to install the driver for 3d acceleration for games and desktop effects. 
System > Administration > Restricted Drivers Manager

---

### Post by peabody on 2007-10-02
> **littlestkiwi said:**
> Hey, just installed ubuntu, loving it so far, just wondering a few things. How do i increase the the resolution? its only at 1024x768 would like to get it a bit higher. Also do i need to install drivers?(would have though you would) and if so were would a good place to get them from be?

We're going to need some information here.  It could be that you'll need the official video drivers of your card to get a better resolution.  It could also be that you're on a widescreen laptop with something like an onboard intel video card, in which case you'll need to install something like the 915resolution package to get your laptop's widescreen resolution (but don't install that if that's not your setup).  This should give you an idea, so please be sure to include as much information about your hardware as you can when you post for help.

Edit: The version of Ubuntu you installed is also important.  Did you install 7.04 or did you opt for the 7.10 beta?

---

### Post by littlestkiwi on 2007-10-02
> **peabody said:**
> We're going to need some information here.  It could be that you'll need the official video drivers of your card to get a better resolution.  It could also be that you're on a widescreen laptop with something like an onboard intel video card, in which case you'll need to install something like the 915resolution package to get your laptop's widescreen resolution (but don't install that if that's not your setup).  This should give you an idea, so please be sure to include as much information about your hardware as you can when you post for help.

Edit: The version of Ubuntu you installed is also important.  Did you install 7.04 or did you opt for the 7.10 beta?

7.04, 64bit version. Cant increase the resoltuion like the other guy said, and downloaded and enabled a restricted driver too.

---

### Post by mindtrick on 2007-10-02
> **littlestkiwi said:**
> 7.04, 64bit version. Cant increase the resoltuion like the other guy said, and downloaded and enabled a restricted driver too.

It's probably your monitor. 
run dpkg-reconfigure xserver-xorg and choose the correct resolution for it.

---

### Post by nickmayfield on 2007-10-02
i used my restricted driver for nvidia geforce 5200 and my resolution went down to 800 by 600? thats my only choice

---

### Post by peabody on 2007-10-02
What is your exact video card and what kind of monitor are you using?  Normal aspect ratio (4:3) or widescreen?  What do you know to be its capable resolution.

---

