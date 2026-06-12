---
title: "Disk Cleanup"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-01-11
Specs of computer:

1.6ghz Intel Core Duo
100gb HD
2gb RAM
256MB Nvidia geforece go 7400

I just downloaded a program called KleanSweep it found about 200mb of files/empy folders that apparently I don't need. But I am too scared to go ahead and delete it.

What are the best options of cleaning up Ubuntu? With windows I would use CCleaner and this would be quite effective and would even speed up some programs.

---

### Post by reckless2k2 on 2008-01-11
i remember using a program like that at one time or another. generally.....anything in a tmp directory "should" be fine. cleanup on tmp stuff is usually done though on boot or after "x" period of time. 

you see linux works a lot different than windows. you don't need that kind of stuff like in windows. you want to keep "clean", police your home directory. that should be fine.

---

### Post by abhiroopb on 2008-01-11
I totally understand that linux does not need cleanup. The thing is that *apparently* there is 200 mb of data that can be deleted....of course I'm too scared to simply delete all of this

---

### Post by HemiGTX on 2008-01-11
If you want to clean your ubuntu machine you need to follow these simple steps to remove all unnecessary junk files.

Remove Residual Config packages

In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to System > Administration > Synaptic Package Manager. On the bottom left hand corner of the window,click the Status button. In the list above the Sections, Status, Search, and Custom buttons, you should see the following text

Installed
Installed(auto removable)
Installed(local or obsolete)
Installed(upgradable)
Not installed
Not Installed (Residual config)

Click on the &#8220;Residual config&#8221; text. (If the &#8220;Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine.

If you want to remove you need to select those packages and click on apply from menu bar Remove packages are in progress.

Remove partial packages

This is yet another built-in feature, but this time it is not used in Synaptic Package Manager. It is used in theTerminal. To access the Terminal, go to Applications > Accessories > Terminal. Now, in the Terminal, key in the following command

sudo apt-get autoclean

Remove unnecessary locale data

For this we need to install localepurge.Automagically remove unnecessary locale data.This is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

Install localepurge in Ubuntu

sudo apt-get install localepurge

After installing anything with apt-get install, localepurge will remove all translation files and translated man pages in languages you cannot read.

If you want to configure localepurge you need to edit /etc/locale.nopurge

This can save you several megabytes of disk space, depending on the packages you have installed.

Example:-

I am trying to install dicus using apt-get

sudo apt-get install discus

after end of this installation you can see something like below

localepurge: Disk space freed in /usr/share/locale: 41860K

Remove &#8220;orphaned&#8221; packages Using GtkOrphan

GtkOrphan (a Perl/Gtk2 application for debian systems) is a graphical tool which analyzes the status of your installations, looking for orphaned libraries. It implements a GUI front-end for deborphan, adding the package-removal capability.

Install GtkOrphan in Ubuntu

First you need to download latest version of GtkOrphan from here using the following command

wget [http://ftp.debian.org/debian/pool/main/g/gtkorphan/gtkorphan_0.4.2-2_all.deb](http://ftp.debian.org/debian/pool/main/g/gtkorphan/gtkorphan_0.4.2-2_all.deb)

Now you have gtkorphan_0.4.2-2_all.deb package you need to install this using the following command

dpkg -i gtkorphan_0.4.2-2_all.deb

At the time of installation you get the following error

dpkg -i gtkorphan_0.4.2-2_all.deb
Selecting previously deselected package gtkorphan.
(Reading database &#8230; 175891 files and directories currently installed.)
Unpacking gtkorphan (from gtkorphan_0.4.2-2_all.deb) &#8230;
dpkg: dependency problems prevent configuration of gtkorphan:
gtkorphan depends on deborphan (>= 1.7.17); however:
Package deborphan is not installed.
gtkorphan depends on libgtk2-gladexml-perl; however:
Package libgtk2-gladexml-perl is not installed.
dpkg: error processing gtkorphan (&#8211;install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
gtkorphan

You need to use the following command to fix

sudo apt-get -f install

This will complete the installation.Once you finished the installation go to System&#8212;>Administration&#8212;>Remove Orphaned Packages

How to use GtkOrphan

Use of GtkOrphan is intuitive and reflects use of deborphan. The screenshots will show you a full example. GtkOrphan must be run with root privilegies.

At GtkOrphan's first run, you should initialize your system in order to keep track of needed packages, even if they are reported as orphaned.
In the main window, expand the "Options" section and check the "Show all orphan packages, not only those in the libs section" checkbox. Note: with this option, GtkOrphan will report as "orphaned" all those installed packages that are not dependencies for any other. In this way, for instance, packages such as gparted, ubuntu-desktop, wine will be listed too, as they are "top-level" packages and no other package depends on them. Now you can traverse this list and right-click->hibernate each package you want to keep and that you don't want to be reported as orphaned anymore. The hibernation list will keep these files and will not show them anymore. You can access and modify the hibernation list as you want, from the View menu or from the right-click popup menu.

---

### Post by crjackson on 2008-01-11
> **HemiGTX said:**
> If you want to clean your ubuntu machine you need to follow these simple steps to remove all unnecessary junk files.

Remove Residual Config packages

In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to System > Administration > Synaptic Package Manager. On the bottom left hand corner of the window,click the Status button. In the list above the Sections, Status, Search, and Custom buttons, you should see the following text

Installed
Installed(auto removable)
Installed(local or obsolete)
Installed(upgradable)
Not installed
Not Installed (Residual config)

Click on the “Residual config” text. (If the “Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine.

If you want to remove you need to select those packages and click on apply from menu bar Remove packages are in progress.

Remove partial packages

This is yet another built-in feature, but this time it is not used in Synaptic Package Manager. It is used in theTerminal. To access the Terminal, go to Applications > Accessories > Terminal. Now, in the Terminal, key in the following command

sudo apt-get autoclean

Remove unnecessary locale data

For this we need to install localepurge.Automagically remove unnecessary locale data.This is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

Install localepurge in Ubuntu

sudo apt-get install localepurge

After installing anything with apt-get install, localepurge will remove all translation files and translated man pages in languages you cannot read.

If you want to configure localepurge you need to edit /etc/locale.nopurge

This can save you several megabytes of disk space, depending on the packages you have installed.

Example:-

I am trying to install dicus using apt-get

sudo apt-get install discus

after end of this installation you can see something like below

localepurge: Disk space freed in /usr/share/locale: 41860K

Remove “orphaned” packages Using GtkOrphan

GtkOrphan (a Perl/Gtk2 application for debian systems) is a graphical tool which analyzes the status of your installations, looking for orphaned libraries. It implements a GUI front-end for deborphan, adding the package-removal capability.

Install GtkOrphan in Ubuntu

First you need to download latest version of GtkOrphan from here using the following command

wget [http://ftp.debian.org/debian/pool/main/g/gtkorphan/gtkorphan_0.4.2-2_all.deb](http://ftp.debian.org/debian/pool/main/g/gtkorphan/gtkorphan_0.4.2-2_all.deb)

Now you have gtkorphan_0.4.2-2_all.deb package you need to install this using the following command

dpkg -i gtkorphan_0.4.2-2_all.deb

At the time of installation you get the following error

dpkg -i gtkorphan_0.4.2-2_all.deb
Selecting previously deselected package gtkorphan.
(Reading database … 175891 files and directories currently installed.)
Unpacking gtkorphan (from gtkorphan_0.4.2-2_all.deb) …
dpkg: dependency problems prevent configuration of gtkorphan:
gtkorphan depends on deborphan (>= 1.7.17); however:
Package deborphan is not installed.
gtkorphan depends on libgtk2-gladexml-perl; however:
Package libgtk2-gladexml-perl is not installed.
dpkg: error processing gtkorphan (–install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
gtkorphan

You need to use the following command to fix

sudo apt-get -f install

This will complete the installation.Once you finished the installation go to System—>Administration—>Remove Orphaned Packages

How to use GtkOrphan

Use of GtkOrphan is intuitive and reflects use of deborphan. The screenshots will show you a full example. GtkOrphan must be run with root privilegies.

At GtkOrphan's first run, you should initialize your system in order to keep track of needed packages, even if they are reported as orphaned.
In the main window, expand the "Options" section and check the "Show all orphan packages, not only those in the libs section" checkbox. Note: with this option, GtkOrphan will report as "orphaned" all those installed packages that are not dependencies for any other. In this way, for instance, packages such as gparted, ubuntu-desktop, wine will be listed too, as they are "top-level" packages and no other package depends on them. Now you can traverse this list and right-click->hibernate each package you want to keep and that you don't want to be reported as orphaned anymore. The hibernation list will keep these files and will not show them anymore. You can access and modify the hibernation list as you want, from the View menu or from the right-click popup menu.


Thanks for this great post...

---

### Post by abhiroopb on 2008-01-12
Agreed this was great, just what I was looking for!

---

### Post by frafu on 2008-02-03
Hello,

There are some residual configs on my system from kernels from the previous release cycle that I am unable to remove: I get the error: subprocess post removal script returned error exit status 1. 

If I try to remove it with "sudo apt-get remove", it tells me that the package is not installed, so it cannot remove it. 

Could anybody tell me how to remove those residual config from previous releases? 

Thanks in advance. 

Francesco

---

