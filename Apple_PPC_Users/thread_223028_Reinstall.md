---
title: "Reinstall ?"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by Power on 2006-07-25
I have a B&W Apple with 512RAM and a 400Mhz CPU.
Currntly :confused: :confused: runing Kubuntu.
I woud like to install ubuntu .It seems more in the way of simple and strong , but i am nolonger able to boot from my CD-ROM. It gives me the option but no acktion. Thank you for your help.

---

### Post by Power on 2006-07-25
I am sorry for my misslabling of this thred.:oops:

---

### Post by linear on 2006-07-25
If you already have Kubuntu running, you should be able to add Ubuntu with the following command (Terminal or shell prompt):

**sudo aptitude install ubuntu-desktop**

(Aptitude, unlike apt-get, will allow you to remove everything you installed if you change your mind.)

---

### Post by anurse on 2006-07-25
I am assuming what you want is the gnome interface because Ubuntu and Kubuntu are the same thing; the difference is the desktop environment and what that brings to you as a user (K, integration and K apps, for instance in Kubuntu). If this is the case, the first thing I would do is reboot. When the log in screen comes up, click on the select session button. If you see an option for gnome session. If so, click on that. If that doesn't work, go into KDE, launch the synaptic package manager and install ubuntu-desktop that way. Its under base system.

---

