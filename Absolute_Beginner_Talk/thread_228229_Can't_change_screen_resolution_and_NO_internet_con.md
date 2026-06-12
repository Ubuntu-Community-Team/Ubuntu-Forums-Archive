---
title: "Can't change screen resolution and NO internet connection!"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by sean_wilson on 2006-08-02
Help.  Just finished installing Edubuntu.

My screen resolution will not allow me to change it.  How do  I change the screen resolution

Also I cannot connect to the internet.
I am currently using an Ethernet cable which is attached to a wireless router which is attached to the modem.

I am using a Windows computer to write this as I cannot connect to the internet.

---

### Post by robglinka on 2006-08-31
Ok one thing at a time.

Don't have a lot of information here, but we'll shoot for the screen resolution thing.

Have you tried System->preferences->screen resolution? You should be able to select from some common screen resolutions from there.

---

### Post by IYY on 2006-08-31
It's strange that your internet connection is not working already, but you can try to set it up in

System > Administration > Networking

You should be able to see your ethernet card (eth0 or eth1), select it as the default gateway device, and turn on DHCP if that's what your router uses (most do these days) or select an IP address.

Screen resolution should be where the above poster pointed. If the higher resolution does not appear in the list, you will need to add it to your /etc/X11/xorg.conf file (will explain how to do it if you ask).

---

