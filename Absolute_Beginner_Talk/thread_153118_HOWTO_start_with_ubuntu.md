---
title: "HOWTO: start with ubuntu"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by frodon on 2006-03-31
Many users install ubuntu and get confused because they don't know how works a debian based distribution.
The purpose of this small guide is to give beginners a summary of needed informations to start with ubuntu.

**[SIZE="3"]1- Ubuntu is a debian based distribution[/SIZE]**

As the title says ubuntu is a debian based distribution, software installation is based on **repositories** and **apt** commands.

**Repository** : A repository is a place on internet where the ubuntu packages are, when you run an "apt-get" command or use synaptic ubuntu will look in the repositories you set to see if the software you want to install is there.

**Synaptic** : Synaptic is a front end for "apt-get" commands and therefore allow you to install/manage/upgrade softwares with a GUI.

**apt-get**: apt-get command lines are used to install/update/manage softwares, it will not be describe here since this guide is for beginners.

**.deb**: a .deb file is a compiled package for debian based distributions, not all .deb are good for ubuntu, you should use first .deb made for ubuntu.

**[SIZE="3"]2- Now, how to install softwares with your internet connection[/SIZE]**

As i said before "apt-get" commands use a repository collection, therefore the first thing to do is to set your repository collection.

**[SIZE="2"]a) Repositories[/SIZE]**

Your repository collection is defined in the source.list file which is in the /etc/apt/ directory.
Now open the file with [root access]("https://wiki.ubuntu.com/RootSudo?"): 
for gnome
```
sudo gedit /etc/apt/sources.list
```
for kde
```
sudo kedit /etc/apt/sources.list
```

Then edit your file like that : ```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
##deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
##deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## uncomment this one for multimedia packages AFTER having finished the upgrade to Dapper.
## deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Dapper PLF
## only uncomment it if you need it
## deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype 
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free

```Each line which start with a "#" is commented and therefore not active.

You may want to enable the plf lines : [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
You may want to enable the backport line : [http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

Save the file and exit, you have now your repository collection set.

**[SIZE="2"]b) Install softwares[/SIZE]**

You're ready now to install softwares.
Go to : **System -> Administration -> Synaptic Package Manager**
[IMG]https://wiki.ubuntu.com/AddingRepositoriesHowto?action=AttachFile&do=get&target=hoarysynaptic.jpg[/IMG]

Once synaptic is opened, press the reload button in order to update the package list, this list will contain all the available packages in the repositories you set.
[IMG]https://wiki.ubuntu.com/AddingRepositoriesHowto?action=AttachFile&do=get&target=PicApplyTheseSettings.png[/IMG]

Now use the search button to find the software you want : 
[IMG]http://i2.tinypic.com/snp6i8.png[/IMG]

Use the right click to choose if you want to install or remove the selected software, then use the Apply button : 
[IMG]http://i2.tinypic.com/snp7au.png[/IMG]

That's all

**[SIZE="3"]2- Now, how to install softwares without internet connection[/SIZE]**

**[SIZE="2"]a) Install a .deb file[/SIZE]**

Download the .deb file corresponding to your software where you want, for the example i assumed you downloaded it to the desktop.

Warning: You may have to install other packages because each software have dependencies (a software need some libraries to work), if you don't have the packages that the software installation requires you will get error messages.

Now, open a terminal and use these commands to install the .deb : ```
cd /home/*username*/Desktop
sudo dpkg -i your_file.deb
```
[COLOR="Red"]
Warning: you can't use the dpkg command if you have synaptic opened at the same time[/COLOR]

**[SIZE="2"]b) Install a .rpm file[/SIZE]**

Sometimes, you may not be able to find the wanted .deb for the software you want and you may only find a .rpm (**R**edHat **P**ackage **M**anager)
Use rpm files only if you can't find a .deb file.

You need first to convert the .rpm file to a debian compatible file (.deb), so you will  need the package called **alien** to do it.
Install it with synaptic or with command lines : ```
sudo apt-get install alien
```
Or find the .deb file and install it with **a)**

Now open a terminal and run these commands to convert the file (assumed you downloaded the .rpm on your desktop) : ```
cd /home/*username*/Desktop
sudo alien <name of program>.rpm
```

and install the generated .deb following **a)**

**[SIZE="2"]c) Install a software from sources[/SIZE]**

Sometimes, if you want the latest release of an apps or if you are unlucky you will find only the sources of the software, generally a .bz2 or a .gz file.

To compile softwares you will need some compiling tools, the package called **build-essential** will install them. Install this package with synaptic or with command lines : ```
sudo apt-get install build-essential
```Or find the .deb file and install it with **a)**

First untar the archive :
for a .gz file ```
tar -xvzf <name of file>
```for a .bz2 file ```
tar -xvjf <name of file>
```It will create a directory with the same name than the archive in most of the cases

Find the README.txt file and the INSTALL.txt file and read both, thoroughly. They will tell you of any dependencies the program may have. Also there should have been information on the site where it came from, especially if it requires a non-standard library or unusual package. (this is what sometimes is known as 'dependency hell' -you can get caught in an endless list of dependencies)

After unpacking the file and being fairly sure that you have what the program requires, build it like so : ```
cd <program dir>
./configure
make
```

Now fully install the software : ```
sudo make install 
```OR```
sudo checkinstall
```
*checkinstall* is not installed by default therefore you will have to install it if you use this way.

Running 'checkinstall' will create the program on the system as a .deb type package which will then appear in synaptic enabling easy uninstallation, and you would be able to create it as your own package and upload it to a website for others to use. When you run 'checkinstall' it will prompt you with a few questions about your name ("maintainer"), YOUR version of the .deb, any revision numbers, conact info (your email address) and of course the package name.

Hopefully now you should have a working installed package, which will need adding to the gnome menus manually using smeg. Don't panic if it doesn't compile first time. Look carefully at the output and see what the program is missing. any questions about errors can always be asked to us; try and paste any errors into your posts and we will be able to explain them to you.

**[SIZE="3"]3- Use the available ressources to solve common issues[/SIZE]**

- **The search field of the forum**
- **The wiki** : [https://wiki.ubuntu.com](https://wiki.ubuntu.com)
- **The UDSF** : [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
- **The unofficial starter guide** : [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)


Thanks for any kind of feedback.


_[SIZE="2"]credits: [/SIZE]_
- **[Bonzodog]("http://www.ubuntuforums.org/member.php?u=44884") **: [http://www.ubuntuforums.org/showpost.php?p=524141&postcount=8](http://www.ubuntuforums.org/showpost.php?p=524141&postcount=8)
- **The wiki** : [https://wiki.ubuntu.com](https://wiki.ubuntu.com)
- **[Mustard]("http://www.ubuntuforums.org/member.php?u=26623")**: for correcting my typo's

---

### Post by OffHand on 2006-03-31
Nice guide to start with. You might want to include the way to get codecs to play media files. (I know it's somewhere else but people are lazy usually.)

---

### Post by mungy on 2006-03-31
thank you for this. it's all starting to make sense :cool:

---

### Post by Mustard on 2006-03-31
I like the mention of the 'checkinstall' method.  It's a little known method and I'd like to see it promoted more by those helping others compile stuff from from source.  It just makes life so much easier with regard to updating to a new version.  I can just uninstall the old version with synaptic, and compile a clean new version (installing with checkinstall again).

---

### Post by johnnymac on 2006-03-31
Agreed...checkinstall is very helpful.  Also...for those who are new to ubuntu - don't forget the wiki - it has most of the "how-tos" for getting your system configured to do most of the "everyday" stuff.

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by zgerrz on 2006-03-31
Quick question with using checkinstall..

After running sudo checkinstall, the program isn't actually installed, correct? Is the output a .deb file that you can install with sudo dpkg -i packagename?

Just asking because it would be nice to be able to cleanly compile and install packages without having to break away from the package management system.

---

### Post by Mustard on 2006-03-31
[QUOTE=zgerrz]Quick question with using checkinstall..

After running sudo checkinstall, the program isn't actually installed, correct? Is the output a .deb file that you can install with sudo dpkg -i packagename?

Just asking because it would be nice to be able to cleanly compile and install packages without having to break away from the package management system.[/QUOTE]

No, the program is installed after running checkinstall, so there is no need to use dpkg -i to install.  It's already done.  Checkinstall does the actual 'make install' part, in addition to that it creates a .deb package, AND installs it.

This is not the limit of checkinstall either, it can create slackware RPM packages.  See the checkinstall web page for details..

[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

---

### Post by gnu2tux on 2006-04-11
Check out my guide for complete newbies at [http://www.linuxnewbieguide.org]("http://www.linuxnewbieguide.org")

Its Linux-generic, but has an emphasis on Ubuntu, and shows the user how to install, configure, use synaptic/etc, install codecs and pretty much everything that a normal day to day computer user would want to know.

I've spent a few years now making it good, and it's a very popular guide, so hopefully it can help ppl here that don't already know about it!

Regards,

Al.

---

