---
title: "Problem configuring downloaded program"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-05-18
Hi 
I'm making attempts to update a program (KMyMoney0.8.6) and I'm having problems configuring it. I get a message which reads

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

I've been advised that I need "the development packages of KDE and Qt".

When I go into the Synaptic Package Manager and look for the above and look for the above I am unsure exactly what I should be downloading.

With KDE it wants to download 281 packages in total. Do I need all those? Secondly with QT I can't see any package with just QT but lots of other ones with QT in them.

Can anyone help me or direct me in the right direction?

Many Thanks
Gazzadtfan

---

### Post by Mrmental on 2007-05-18
You might try installing xorg-dev. It'll be smaller, but beware, it's experimental. Make sure you back up your original xorg configuration, which is in /etc/X11/xorg.conf
This is the address: [http://packages.debian.org/experimental/x11/xorg-dev](http://packages.debian.org/experimental/x11/xorg-dev)

---

### Post by Bachstelze on 2007-05-18
The xorg-dev you install using the standard Ubuntu repos is certainly not experimental ! And it has nothing to do with the xorg.conf either.

---

### Post by gazzadtfan on 2007-05-18
Hi

has anyone else any ideas?

gazzadtfan

---

