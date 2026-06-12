---
title: "Ati 8.32.5 driver for 6.10"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Sellout on 2007-01-26
x800xt AIW
va1912wb 19" lcd

after I install the ATI proprietary driver and reboot, the screen's vertical refresh for some reason is 30 and wont display, 
so i run "dpkg-reconfigure xserver-xorg" and set the refresh that way, it boots to the login screen but after I enter my pwd i get an error that my session lasted less than 10 seconds with the error:

" .: 106: Can't open /etc/profile"

soooo i start a failsafe session to reinstall the ati drivers. Since they dont "natively" support anything but redhat and suse, i use the ati directions to install on a different build..here's where i'm stuck:

[I]dave@link:~/Downloads$ sudo sh ./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/6.10
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/6.10
./packages/Ubuntu/ati-packager.sh: 176: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install
dave@link:~/Downloads$ [/I]

any help from here would be great :)

---

### Post by Sellout on 2007-01-26
bingo
[http://www.ubuntuforums.org/showthread.php?t=331333&highlight=can%27t+open+%2Fetc%2Fprofile](http://www.ubuntuforums.org/showthread.php?t=331333&highlight=can%27t+open+%2Fetc%2Fprofile)

---

