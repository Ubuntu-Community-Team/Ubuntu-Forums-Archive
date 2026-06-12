---
title: "[SOLVED] iMac G3 600 MHz Ubuntu 8.04 screen init failed"
date: 2008-09-20
forum: Apple Hardware Users
---

### Post by shulmice on 2008-09-20
Hi;
I have a iMac G3 600 MHz, 1 Gig of Ram 60 Gig HD dual boot with Mac OS 10.4.11
I have installed Ubuntu 8.04-1 Alternate-PowerPC.
the screen is blank and then flashing, then I get a command line stating "screen init failed" 
I have run dpkg-reconfigure xserver-xorg and it stops after the keyboard, saying something about overwriting files. 
I have done this a root and in sudo.
I have manually edited the /etc/X11/xorg.conf files as posted on the forums without any luck.
I have downloaded the ATI drivers as suggested and I get an error message about overwriting files.
I have tried everything from Xubuntu 6.06 Alternative to 8.04 Live CD without any luck.
Does anyone have any suggestions?
Solved: Burn 6.06.1 Live CD on the lowest speed setting on Toast.
Follow the posts about hitting alt + opt + F1 keys and edit the xorg.conf file by typing sudo nano /etc/X11/xorg.conf then hit enter key
[COLOR="Red"]Change the load "dri" to #load "dri"
Change HorizSync to 59-61 and VertRefresh to 75-117[/COLOR]
hit ctrl+o, enter, ctrl+x then 
[COLOR="Red"]sudo killall -HUP gdm[/COLOR]
After you have a desktop double click on  install and follow the instructions. One hint:
you can duel boot with Mac OS X and Mac OS 9 by setting as much disk space as FREESPACE and letting Ubuntu partition the drive. It will allocate space for a boot loader, the main drive and a swap area.[COLOR="Red"][/COLOR]
follow the instructions. 
After installing, removing the CD and rebooting. hit ctrl + Alt + F2 and run sudo apt-get update and then sudo apt-get upgrade.
Thank you to everyone who has posted help in this area.:lolflag:[COLOR="Red"][/COLOR]

---

