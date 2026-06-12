---
title: "How to uninstall Video drivers from command line?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by spectrum48k on 2007-06-24
If X Server fails because of incorrect video driver, how does one go about removing the offending driver?

---

### Post by atria on 2007-06-24
What is the driver? Use aptitude/synaptic to remove it.

Also you can instruct X to use a generic driver in place of the offending driver by:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by spectrum48k on 2007-06-24
It is an NVIDIA driver I don't know specifically which one as it was installed automatically by ENVY.

Thanks

> **atria said:**
> What is the driver? Use aptitude/synaptic to remove it.

Also you can instruct X to use a generic driver in place of the offending driver by:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by atria on 2007-06-24
I see, you might want to check out the ubuntu community wiki for installation of nvidia drivers. The tutorial worked fine for me.

Welcome, its my pleasure to help ;)

---

### Post by spectrum48k on 2007-06-24
I tried the code you gave me and picked VGA on low res but still have the same problem as before.  What am I doing wrong?  It all just got very frustrating!!!....was really enjoying UBUNTU too..

> **atria said:**
> I see, you might want to check out the ubuntu community wiki for installation of nvidia drivers. The tutorial worked fine for me.

Welcome, its my pleasure to help ;)

---

### Post by bodhi.zazen on 2007-06-24
What nvidia card do you have ?

Usually one installs the Nvidia driver (envy is fine). Let the install script configure X.

Otherwise you can configure the nvidia driver with :

```
sudo nvidia-xconfig
```

If that fails, we need to know your video card, monitor, and post xorg.conf

---

### Post by VincentvanG on 2008-04-27
> sudo dpkg-reconfigure -phigh xserver-xorg

this worked for me, thanks man!

---

