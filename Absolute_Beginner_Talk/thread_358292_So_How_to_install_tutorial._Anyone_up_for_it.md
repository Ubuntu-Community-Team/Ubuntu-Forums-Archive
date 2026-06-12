---
title: "So? How to install tutorial. Anyone up for it?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by coldopm on 2007-02-10
I have a question.

I am have finally made the transition from Windows to Linux, I use Edgy distro.

When I download a software package, for example video drivers meant to run in Linux from a website and I have the file on my desktop, how can I then run that file or install the specific software package that I downloaded?

Please help, but try to be gentle, I am slowly losing my virginity here!

Thank you!

---

### Post by r4ik on 2007-02-10
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

or

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Good luck !

---

### Post by aysiu on 2007-02-10
These two guides may come in handy:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by coldopm on 2007-02-10
Installing downloaded packages

Sometimes you might want to install a package which you have downloaded from a website, rather than from a software repository. These packages are called .deb files. Because they may have been created for a different Linux distribution, they may have unmet dependencies on Ubuntu and so may not be installable.
Using GDebi to install packages

GDebi is a graphical application used to install packages. It automatically checks packages for their dependencies and will try to download them from the Ubuntu software repositories if possible. You may first need to install GDebi - simply install the gdebi package using one of the package managers listed above, or open a Terminal and type sudo apt-get install gdebi.

Once you have installed GDebi, use the File Browser to find the package you wish to install. Package files will look similar to this:

deb_package.png

Double-click the package to open it with GDebi. If all dependencies have been met for the selected package, simply click the 'Install package' button to install it. GDebi will warn you if there are unmet dependencies.
Using the Kubuntu Package Management Utility

To install a .deb file in Kubuntu, right-click on the .deb file, and choose Kubuntu Package Menu->Install Package.
Using dpkg to install packages

dpkg is a command-line tool used to install packages. To install a package with dpkg, open a Terminal and type the following:

cd directory 
sudo dpkg -i package_name.deb

Note: replace directory with the directory in which the package is stored and package_name with the filename of the package.

It is recommended that you read the dpkg manual page before using dpkg, as improper use may break the package management database. To view the manual page for dpkg, open a Terminal and type man dpkg. 

Thank you!

---

### Post by Amnon82 on 2007-02-10
Well it depends in which form you downloaded the software. There many types out there.

Sourcecode:

Mostly they are in tar-files also called tarballs. You have to extract them and compile the software with the rule of three: .configure - make - make install

Binaries:

They also can be in tar-files. Extract them and change there mode to be executable.
The easiest way is right-click on the file and change the Properties to "Allow executing file as program" in the Permissions-Tab.

Deb-Packages:

This is the simplest way to add a program. Packages are precompiled binaries. The packagemanager copies the files in the way so a user can execute the program via clicking on a Link like in Windows (here in linux it is called .desktop-file). To install a Deb-Packages in Ubuntu simple double-click it and follow the instructions.

RPM-Packages:

Same as Deb-Packages but for another Distro like RedHat or Suse. You can convert them with a program called alien to a Deb-Packages and which versa, but it is always better to use a Deb-Packages which is build for Ubuntu.

---

### Post by aysiu on 2007-02-10
Please name the package you're trying to install.

Thanks.

---

