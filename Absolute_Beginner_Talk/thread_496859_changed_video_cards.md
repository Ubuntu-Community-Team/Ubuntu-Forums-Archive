---
title: "changed video cards"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by knotman on 2007-07-09
and now i cant boot when i do this comes up

scott@scott-desktop:~$

i went from a nvidia to a ati radeon 9800 xt

---

### Post by overdrank on 2007-07-09
> **knotman said:**
> and now i cant boot when i do this comes up

scott@scott-desktop:~$

i went from a nvidia to a ati radeon 9800 xt

HI if you changed video cards then you need to reconfigure you xorg
by running this command
```
sudo dpkg-reconfigure xserver-xorg
```
Answer a few questions and you should be up and running after reboot
```
sudo shutdown -r now
```

---

### Post by knotman on 2007-07-09
should i type this after the scott@scott......  ?

---

### Post by zero244 on 2007-07-09
Well if you just changed cards that wont work.
If you installed drivers for your Nvidia card you should uninstall them. 
For now I would try to edit your xorg.conf file so you can get back in to your desktop.
What you need to do is change the line in the device section of your xorg.conf file
the line is
Driver       "nv" or it might be "nvidia"
You need to change it to "vesa"
To do this type this in the terminal .............the black hole of Linux where your stuck now.
sudo nano /etc/X11/xorg.conf
password what ever your password is.
Now nano is a very basic text editor, look for the driver line in the device section and change it to vesa with the quotations. And save the file.
exit out of nano.
The type sudo shutdown -r now
To reboot
One thing you can do if nothing else works is delete the xorg.conf and it should default to a vesa driver.
There probably already is a backup of your xorg.conf tile. If not type this in terminal before you delete it.
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak1
Now to remove it
cd /etc/X11
sudo rm xorg.conf
then
sudo shutdown -r now
Let up know if you get it back running.

---

### Post by overdrank on 2007-07-09
> **knotman said:**
> should i type this after the scott@scott......  ?

first you will have to login user name and password

---

### Post by knotman on 2007-07-09
yes i did uninstall the drivers for nvidia first

---

### Post by zero244 on 2007-07-09
The above post suggested you type this

sudo dpkg-reconfigure xserver-xorg

Give it a try and see if it works
If you can get into the configuration app you can change to a vesa driver from there.
If you cant then you will have to manually change the driver line or delete the file.
If you get into the xserver-xorg it will ask you for information. Just keep answering the questions best you know how. Usually the default is right, except for the driver be sure and select the vesa driver.

---

### Post by zero244 on 2007-07-09
If you can get back into Ubuntu you can then install the ATI drivers instead of the vesa driver which will not give you any speed at all.
I forget if the xserver-xorg config utility gives you a choice for a ATI driver if it does you can select that one.
Im running a Nvidia card and used Automatix2 to install my video drivers.........you can install ATI drivers as well.

---

### Post by knotman on 2007-07-09
i did it the easy way i had nothing but the updates so i just reformatted and reinstalled i did do what overdrank susjested and it worked but i did something else and messed up the mouse ( it wouldn`t move) so i decieded to wipe it out 


thanks for the help

---

