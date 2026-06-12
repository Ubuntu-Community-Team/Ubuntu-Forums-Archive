---
title: "Ubuntu 12.10 &amp; 13.04 64 bit Bricscad 13 and Draftsight install instructions that work"
date: 2013-05-22
forum: Art &amp; Design
---

### Post by mjharold on 2013-05-22
Bricscad 13 64 bit and draftsight 2d free works on Ubuntu 12.10 and 13.04 64 bit by directions below




Bricscad-v13.1.19on Ubuntu 12.10 x64 wubi install in terminal mode after su or root password. Cut and paste each command line and then enter.  Repeat for each command until all have been executed below:


sudo dpkg--add-architecture i386


sudo apt-get update




This installs the ia32-libs and ia32-libs-multiarch needed. As I read, the wubi install of ubuntu 12.10 does not include the i386 and does not allow the single packages, you have to have all to get all dependencies as I understand.




I then installed gdebi installer rather than the default ubuntu software center package installer.




after that I right mouse clicked over the downloaded BricsCAD-V13.1.19-2-en_US-amd64.deb file and selected install with gdebi installer.




It installed complete with no dependency errors or any comments. Found the icon and added to sidebar. launched and it came up with no errors and did not die during exercising bricscad. I seem to have true type fonts also. 




Draftsight 2d (free) Install Ubuntu 12.10 64 bit (WUBI) and Ubuntu 13.04 64 bit (full install, not WUBI) works both by the following:




After the above bricscad terminal commands above I did the following:
download 32 bit .deb file to install from [http://www.3ds.com/products/draftsig...ad-draftsight/](http://www.3ds.com/products/draftsig...ad-draftsight/)
after downloading (this file will be in the downloads directory) install via terminal mode and provide root or su (superuser) password
then type or paste following and enter after each command to execute.


sudo apt-get install ia32-libs libdirectfb-extra libxcb-render-util0


sudo dpkg --force-all -i ~/Downloads/draftSight.deb


sudo apt-get -f


installed, found icon via installed applications, added icon to sidebar, launched....it worked. This version is pre-release of commercial and may not be free later (read the license) but cool to play with until they charge. 
Good luck




Following both above for Ubuntu 13.04 64 bit (full install, non WUBI) I had a dependency error in 13.04 so I did the following to get Bricscad 13 64 bit to install and work by the following in terminal mode:


sudo dpkg --force-all -i ~/Downloads/BricsCAD-V13.1.19-2-en_US-amd64.deb


sudo apt-get -f




Worked.  I am sure if not a novice to linux this could be done cleaner but it works so hoping to help others on these programs to function succesfully.


Bricscad 13 on ubuntu 13.04 64 bit full install (not WUBI)
I believe these command lines would instead of the above commands for Bricscad 13 64 bit could be don and not have the dependency error and work first time by the following:


sudo dpkg--add-architecture i386
sudo apt-get update
sudo dpkg --force-all -i ~/Downloads/BricsCAD-V13.1.19-2-en_US-amd64.deb
sudo apt-get -f


I did not try this as I already had it working.  Good luck

---

### Post by dino99 on 2013-05-22
[http://bricsys.com/common/knowledge/topic.jsp?id=305](http://bricsys.com/common/knowledge/topic.jsp?id=305)

---

### Post by sandyd on 2013-05-22
**Moved to Art & Design**

---

