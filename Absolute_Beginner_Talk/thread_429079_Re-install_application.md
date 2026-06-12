---
title: "Re-install application?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Ahunt on 2007-04-30
I have a downloaded application that is seized up and isn't working right. It was downloaded though the command line interface.

I have the .deb package. Can I just re-install the package to replace the existing files or do I have to uninstall the existing package first? and then re-install?

Adam

---

### Post by taurus on 2007-04-30
It depends on how you installed the package initially.  If you installed it with synaptic/apt-get/aptitude, then use the same method to remove it first.  If you installed it as .deb, then use "dpkg -r package_name" to remove it.  It's better to remove the old version before installing the new one but of course, you can always go ahead and install the new one and see if it works now.

---

### Post by Ahunt on 2007-05-01
Thanks for that information. The package is AVG anti virus and it was installed from the command line, since it is not in the add/remove or synaptic repositories. I followed the instructions at [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064) and it installed just fine and runs well. It locked up while downloading update files a couple of days ago and will not unlock, hence the need to reinstall it.

I tried reinstalling the package without removing it and got nothing but errors, but it was worth a try.

So I tried using your suggestion there to remove it (which is the same procedure as the Desktop guide) here is the result I got:

~$ sudo dpkg -r avg75fld-r45-a0973.i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

What is the best way to proceed now? 

The original instructions to install it were:
 
Installation

Download The Free AVG Advisor from here (.deb) to your Desktop.
Code:
cd ~/Desktop
sudo dpkg -i avg75fld-r45-a0973.i386.deb


Launcher

Making a launcher to start AVG
Code:
sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktop
add:
Code:
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
save and exit by (Control-X, Y, Enter). 

and so it was installed at /usr/bin but there are 1309 files in that folder and I have no idea which ones to specify.

Any help would be greatly appreciated!!

Adam

---

### Post by Ahunt on 2007-05-01
Hi again:

Further to my last post here:

I have done some more digging and according to the AVG forum uninstalling the application and then re-installing it won't solve the problem. I got a command line from that forum that fixes the problem, until I try to download one particular update file and then it locks it up again. The command then again unlocks it. It is a bit of a circle. I think the problem is one update and that the problem is on their end not on my PC.

I am going to pursue this on the AVG forum and see what I can find out.

Thanks again for your help here - this is a great resource!

Adam

---

