---
title: "Installing Vista through VirtualBox"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-12-09
Where/how can I install/find Windows Vista through VirtualBox?

---

### Post by overdrank on 2007-12-09
> **RobotoWorks said:**
> Where/how can I install/find Windows Vista through VirtualBox?

Hi and here is a good link
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
Good luck!

---

### Post by RobotoWorks on 2007-12-09
Once I have this installed properly, will it run slow, or normal speed? I have 1.5 Gihs of RAM.

---

### Post by overdrank on 2007-12-09
> **RobotoWorks said:**
> Once I have this installed properly, will it run slow, or normal speed? I have 1.5 Gihs of RAM.

I can not speak on vista but I have installed Windows 2000 and it ran ok.

---

### Post by Bandicoot on 2007-12-09
Depends on the amount of memory you will give the virtualized Vista.. Seeing that you have 1,5 GB of ram I do not think it will run ultra smooth, but that is because Vista is very resource hungry ..

---

### Post by RobotoWorks on 2007-12-09
Im following the tutorial you gave me step by step, Im still at the beginning where  have to install the OSE, how ever when I entered the Sudo code it gave me I got the following:

Done!
unpack 
Extracting the package tarball, /usr/src/virtualbox-ose.tar.bz2, please wait...
Target package file 
/usr/src/virtualbox-ose-modules-2.6.22-14-server_1.5.0-dfsg2-1ubuntu3+2.6.22-1
4.46_i386.deb already exists, not rebuilding!
(however, you could use the -f switch to ignore it)
dpkg -Ei /usr/src/virtualbox-ose-modules-2.6.22-14-server_1.5.0-dfsg2-1ubuntu3+2.6.22-14.46_i386.deb 
dpkg: regarding .../virtualbox-ose-modules-2.6.22-14-server_1.5.0-dfsg2-1ubuntu3+2.6.22-14.46_i386.deb containing virtualbox-ose-modules-2.6.22-14-server:
 virtualbox-ose-modules-2.6.22-14-generic conflicts with virtualbox-ose-modules
  virtualbox-ose-modules-2.6.22-14-server provides virtualbox-ose-modules and is to be installed.
dpkg: error processing /usr/src/virtualbox-ose-modules-2.6.22-14-server_1.5.0-dfsg2-1ubuntu3+2.6.22-14.46_i386.deb (--install):
 conflicting packages - not installing virtualbox-ose-modules-2.6.22-14-server
Errors were encountered while processing:
 /usr/src/virtualbox-ose-modules-2.6.22-14-server_1.5.0-dfsg2-1ubuntu3+2.6.22-14.46_i386.deb

I: Direct installation failed, trying to post-install the dependencies

apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xchat-gnome-common dia-libs xchat-common gnome-splashscreen-manager tcl8.4
  dia-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by Bandicoot on 2007-12-09
No I don't think it will run ultra slow, although it depends alot on the rest of your hardware ofcourse. The best way to find out how well it runs on your system is to just try it. A vista install will take about 35 minutes so why not just try it out.

Edit: you just changed your post so this answer loks a bit out of place.

---

### Post by RobotoWorks on 2007-12-09
Hmm, I honestly dont know how to install this, when ever I type in codes from the tutorial, I get errors from terminal, and I dont know whats causing them.

---

### Post by Bandicoot on 2007-12-09
The OSE edition is in the repositories ( I'm running Gutsy and I can install it via Synaptic) so that's will be the easiest way to install .. BTW the OSE edition lacks a few functions, one of them being usb support, you can downlaod a .deb from the virtualbox site for Gutsy which has all features.

---

### Post by RobotoWorks on 2007-12-09
By OSE, do you mean the OSE if Vista or VirtualBox?

---

### Post by overdrank on 2007-12-09
> **RobotoWorks said:**
> By OSE, do you mean the OSE if Vista or VirtualBox?

You may try here also and it has a user manual that will help
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Bandicoot on 2007-12-09
As far as I know there is no open source edition (ose) of Vista .. Would be great if there was :)

---

### Post by RobotoWorks on 2007-12-09
Lol, okay, so what how exactly do I install this? As I said before I tried to follow the tutorial but it just gave me terminal eroors and nothing was done.

---

### Post by Bandicoot on 2007-12-09
Just download the .deb  from the virtualbox site, you can simply doubleclick it and it will install ..you can use the tutorial to see what you have to do after it is installed. If you wish to use the OSe version just go to synaptic do a search for virtualbox and install it via synaptic, no need to follow the instructions how to install it then.

---

### Post by RobotoWorks on 2007-12-09
I already have VB installed, and its been installed for a while, now I want to know how to run Vista on it.

---

### Post by Bandicoot on 2007-12-09
hmm very confusing , the rpoblems you mentioned earlier were related to the install of VB .. To run vista just insert the vista disc, or image and install it ..what problems are you having with installing Vista ?

---

### Post by RobotoWorks on 2007-12-09
Well how do I get it, I mean I dont want to dual boot it, just run it off of VB, where do I get the files to install it?

---

### Post by overdrank on 2007-12-09
> **RobotoWorks said:**
> I already have VB installed, and its been installed for a while, now I want to know how to run Vista on it.

Then you may look at the link I posted and mention _user manual_ at the virtual box site. :KS

---

### Post by RobotoWorks on 2007-12-09
So VB, has the files all ready, and now its just a matter of installing them?

---

### Post by Bandicoot on 2007-12-09
:lolflag: no offcourse not ! You have to pay for Vista ( big bucks) so they will not include it in a program .. To install vista you will have to own a copy of Vista.

---

### Post by RobotoWorks on 2007-12-09
i dont have m own copy, sorry I thought since this was not actually dual botting and only VB Vista that they wold make some sort of freeish Vista just for VB.

---

### Post by Bandicoot on 2007-12-09
No. As with every MS product you pay for the licence to use the OS. That you are not dual booting but using it in a Virtual Machine makes no difference you are still using the OS ergo you you still have to pay the licence fee.

Above is one of the reasons MS has so much money. : )

---

### Post by RobotoWorks on 2007-12-09
Got it, if I ever decide to purchase it, then I will install it :)

---

