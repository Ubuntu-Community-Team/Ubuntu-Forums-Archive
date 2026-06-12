---
title: "Xserver"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-10-04
Hi,

I tried to insall XGL + Beryl yesterday messed up my Xserver, following this guide.

[http://ubuntuforums.org/showthread.php?t=268036&highlight=beryl+ATI](http://ubuntuforums.org/showthread.php?t=268036&highlight=beryl+ATI)

I know it was stupid, because I have a ATI radeon 9800 pro card, but I gave it a shut anyways, without the Nvidia part.

This messed up my Xserver, or atleast when loggin in, XGL didnt load and Beryl didnt load either, but everthing ran REAL SLOW.

So I tried to fix it, by removing the stuff I installed this way:

> aktiwers@HAL:~$ sudo apt-get remove  xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes

Then I changed the stuff I added in the different .config files back to normal.
Then rebooted, and the xserver was totally broken. Couldnt even get to the login screen. So I messed around in the Terminal and managed to get to the login screen. This time its not running slow, but it is a way to small Screen Resolution, and I cant pick higher. 

I then tried to install the ATI drivers, but it now gives me this error message:

> aktiwers@HAL:~$ sudo sh ./ati-driver-installer-8.29.6.run Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
aktiwers@HAL:~$ 

Anyone has an idea how to fix this? If removing ALL Video drivers, and everthing related to xserver and installing again, is the only option, I am open for that. I just want to save my current Theme :)

Any ideas anyone? Please tell me if I need to post more info, as I quite stuck here.

Thanks a lot!

---

