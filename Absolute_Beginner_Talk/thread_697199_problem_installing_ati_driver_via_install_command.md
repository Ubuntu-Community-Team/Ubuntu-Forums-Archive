---
title: "problem installing ati driver via install command"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
 After successfully(??) installing an analog Lucent modem drivers with gnome terminal,I subsequently lost my video card driver!!

I downloaded an ATI Radeon installation.run file,and tried to install it with sudo aptitude-not with apt-get which may be the reason for the following output log:

rom@rom-desktop:~/Desktop$ sudo aptitude install ati-driver-installer-8.28.8.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "ati-driver-installer-8.28.8.run"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

I need to know if the error unable to find the ATI file(filename)was caused by using aptitude instead of apt-get which was indicated in another topic posted elsewhere??

---

### Post by taurus on 2008-02-14
Why not just run

```
cd ~/Desktop
chmod 755 ati-driver-installer-8.28.8.run
sudo ./ati-driver-installer-8.28.8.run
```

---

### Post by PeterJS on 2008-02-14
Aptitude is for installing packages from the repositories, not for running random programs that have the side effect of installing software. If you wanted to install fglrx with aptitude you would use:
```

sudo aptitude xorg-driver-fglrx

```

The program for building packages from third party installers is checkinstall, so to use check install in this case you would use:
```

sudo checkinstall ati-driver-installer-8.28.8.run

```

---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
  I probably should have used check install rather than aptitude install.but I did try the following command in gnome terminal with the dismal results:

rom@rom-desktop:~/Desktop$ sh ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
rom@rom-desktop:~/Desktop$ 

These results may be due to the fact the ATI drivers are for the 8500 series Radeon-up video card, where my card is the ATI Radeon mobile 7500 series AGP card!!
I will probably need to go back online to find ATI Radeon drivers compatible with Ubuntu/Linux

P.S.
Here is the result of using PeterJS's checkinstall code to install the ati package:

rom@rom-desktop:~/Desktop$ sudo checkinstall ati-driver-installer-8.28.8.run
[sudo] password for rom:
sudo: checkinstall: command not found
rom@rom-desktop:~/Desktop$ 

Might be the syntax is wrong or I am missing the checkinstall command as well
as my ATI drivers which were installed when first installing Ubuntu on my computer!!

---

### Post by PeterJS on 2008-02-14
Ubuntu uses dash (not bash like everyone else) as it's default sh, so it's entirely possible that the script uses a bash specific feature and won't work with dash. Also, you're going to be installing drivers into a system wide location this is not something a normal user account can do, you will need to elevate the privilages with sudo.
```

sudo bash ati-driver-installer-8.28.8.run

```


**PLEASE** read about the package system and installing things
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
**PLEASE** read about about how root, sudo, and the privilege system works
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you have questions please ask, but you are going to need to have at least a cursory grasp of the theory of how a linux system works.

EDIT in response to an EDIT:
checkinstall is not installed as part of the base system but can be installed with:
```

sudo aptitude install checkinstall

```

---

### Post by RoBo5050 on 2008-02-15
Hello forum members,
  I found an article on the ubuntuguide.org site that pointed me in the
right direction ;the ati driver package I needed to install had been blacklisted according to the article,and that I ran some code in reference to the compiz fuz(??)ion desktop app that need  to be configured to
accept the Radeon drivers as well as cleaned up some problems with
the source files!!

After I rebooted  aftyer using the terminal,I was greeted with my old high resolution enhanced desktop/splash screen,etc!!!:)

This problem is officially solved(unofficially)!!

---

