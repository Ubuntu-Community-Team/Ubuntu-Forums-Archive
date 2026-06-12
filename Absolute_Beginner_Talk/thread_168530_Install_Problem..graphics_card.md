---
title: "Install Problem..graphics card?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by gRiMgRaVy014 on 2006-04-30
I have a Pentium 3 1.0ghz 384ram and a 40 gig HDD, with a PCI Nividia Geforce 5500 FX oc.
I'm fed up with windoze and decided to take the Linux route.
The overall install went normal no error or anything.However when I tried to actually start Ubuntu it froze with a command line and didn't let me input anything into the command line. I think it might be my graphics card. Is it possible to install Ubuntu using my intergrated graphics and then configure Ubuntu to use my Nvidia card later?
However I'm not even sure if its my graphics card, it could have just been a bad install.

Please Help!

---

### Post by muep on 2006-04-30
You should be able to log in in text mode. Type in your user name and press enter. It then asks your password but won't show any stars or other characters as you type it. It anyway reads it, just type the password and press enter. You now should get into the command line.

Now some commands:

sudo reboot
reboots your computer, so no need to reset it. Sudo command asks for your password, just as login asked.

sudo dpkg-reconfigure -phigh xserver-xorg
should reconfigure xorg, the graphics system. After this you should try:

sudo /etc/init.d/gdm restart
which restarts the graphical login process.

If this won't help, you may try:

sudo dpkg-reconfigure xserver-xorg
this is a bit more manual way to reconfigure xorg. It asks you many questions, usually you can just answer the default if you don't know the answer. Try different drivers. nv is a free driver for Nvidia cards. vesa works with almost any card.

If this doesn't help, you need to install Nvidia's own drivers for your card. You probably will want to do this anyway at some point.
First, install the driver with the commands:

sudo apt-get update
sudo apt-get install nvidia-glx

Then, use sudo dpkg-reconfigure xserver-xorg to select the newly installed driver. It is called nvidia.

Now restart gdm with the command:

sudo /etc/init.d/gdm restart


come here and ask for more help if you need :)

---

