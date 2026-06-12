---
title: "How To Get GNOME Running On Ubuntu Server"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by helpee on 2007-10-28
There seems to be no consolidated list of commands to get GNOME running on Ubuntu Server, so I saw an opportunity for my first How To :P


You may need to press Return now and again or enter your superuser password, so don't just run this and walk away. Once you have server installed, login to your user account, insert the Ubuntu Server CD to your cdrom drive, run the following commands & follow any given directions as needed:

# sudo apt-get update
# sudo apt-get install ubuntu-desktop
# sudo apt-get install gdm
# sudo /etc/init.d/gdm start

Login to GNOME with your username and password, open a terminal in Applications>Terminal on your top menu bar and enter the following command (following directions and entering your superuser password as needed):

# sudo dpkg-reconfigure xserver-xorg

Presto, you get to double click on things again! Enjoy.

p.s. KDE should probably work by just replacing 'gdm' with 'kde' everywhere, but no promises.

---

### Post by Six_Digits on 2007-10-28
Good tip :)

---

