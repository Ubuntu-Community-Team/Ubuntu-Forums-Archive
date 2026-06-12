---
title: "Install ATI R9000 Pro Card driver, please look :)"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-07-10
I have downloaded the *ati-driver-installer-8.28.8.run* (I've read this is the last supported version for my card. I could go ahead and run it, but I'm afraid that I'll screw up once again and x server will hang after reboot. 

PLEASE tell me what to do, because I'm pretty desperate. I've tried the [official wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way") but it stops here: > boris@buck:~/Desktop$ sudo bash ati-driver-installer-8.28.*.run --buildpkg Ubuntu/feisty
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


What should I do? Thanks.

---

### Post by Kubunteando on 2007-07-10
Don't worry. That command would create the Debian packages only, but it will not install them.
So yo have not modified your system. It is just as before.

The bad news it that your card (same as the one I use, an ATI Radeon Mobility 9000) are last supported on those 8.28 ATI drivers. And those do not work with the new kernel versions, for example the one in Feisty.

So go for the Open Source drivers, you will have also a good 3D performance, although some features will be missing. But you can use almost all the 3D Applications and Games with them (I recommend to use MESA 6.5.3 instead of the default 6.5.2 that comes with Feisty). The Open Source drivers should be installed by default in a fresh installation of Feisty, and at least I got 3D HW acceleration working out of the box.

Install "driconf" from the repositories and enable "HyperZ buffer", that will increase the performance.

---

### Post by Boris-- on 2007-07-10
Aha, that's the problem, thanks for clearing it up for me. My biggest wish is to get TV-out going, but I didn't look into that yet, is this possible with MESA?

Thanks again for your time.

---

### Post by Kubunteando on 2007-07-10
Look for GATOS. That is the name of the project to get TV Out with the MESA drivers on legacy ATI cards.

[http://ubuntuforums.org/showthread.php?t=215763](http://ubuntuforums.org/showthread.php?t=215763)

Check the link above, but again that one it seems to be for Edgy, not for Feisty.

In my case I have not tried to get TV-out.

---

### Post by Boris-- on 2007-07-10
I'm looking at these new MESA drivers now and noticing that there is a 7.0 version out. It's ok to use this one, right? :KS

---

### Post by Kubunteando on 2007-07-10
Yes, it is ok.

In my case I tested it and I didn't find any improvements, since the radeon driver does not support OpenGL 2.0 when using 3D HW acceleration...

And I had the feeling that 7.0 was consuming more CPU, so I went back to 6.5.3, since I didn't have any problems with that one. But 6.5.3 is a development release, and 7.0 is a stable release.

---

