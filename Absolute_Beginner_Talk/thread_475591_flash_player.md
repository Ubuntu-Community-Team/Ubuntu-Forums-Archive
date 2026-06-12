---
title: "flash player"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-06-16
I have try to do what someone told me to do on the forum and here's what i get in terminal.....

gprok@gprok-desktop:~$ sudo aptitude install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
gprok@gprok-desktop:~$ 


i still dont see flash in firefox.............i must be doing something wrong hehehehe

Gprok  TIA !:popcorn:

---

### Post by Happy_Man on 2007-06-16
Hmmm..... have you tried ubuntu-restricted-extras? That installs flash, as well as java and media codecs. I'm only asking you to install to see whether it's a server problem or your computer's problem.

---

### Post by gprok on 2007-06-16
although im  a computer freak im a TOtal newB to linux and ubuntu restricted extras mean nothing to me at the moment.........is it a package i have to install ???  TY for your help happy_man

Gprok

---

### Post by Happy_Man on 2007-06-16
Yes. From a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sailor2001 on 2007-06-16
I assume you are using firefox.......Click your add-ons and download grease monkey..... Follow it's instructions to manage users scripts

---

### Post by carloslosgrande on 2007-06-16
Hi Gprok, have you looked in [COLOR="Blue"]applications>add/remove apps[/COLOR]?
This is where I got [COLOR="Red"]flash plugin-nonfree[/COLOR], ie adobe.
see this;
>  Macromedia Flash plugin
Adobe Flash Player plugin installer  
This package will download the Flash Player from Adobe.
It is a Netscape/Mozilla type plugin.
Any browser based on Netscape or Mozilla can use the Flash plugin.
This package currently supports the following browsers: Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.
Also Galeon and Epiphany can use the Flash plugin.
Konqueror can also use the Flash plugin if konqueror-nsplugins is installed.
WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be downloaded from [www.adobe.com](www.adobe.com).
The distribution license of the Adobe flash plugin is available at [www.adobe.com](www.adobe.com).
Installing this Ubuntu package implies that you have accepted the terms of that license.

[COLOR="Blue"]add/remove[/COLOR] is really good and has most of the stuff you'll need, certainly to begin with.
I like to keep things as simple as possible.

---

### Post by chemtut on 2007-06-16
download it from synaptic
search for flashplugin-nonfree

---

### Post by gprok on 2007-06-16
gprok@gprok-desktop:~$ sudo aptitude install flashplugin-nonfree
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
gprok@gprok-desktop:~$ 


i try installing the package with sudo apt-get install ubuntu-restricted-extras   AND i got the error that i cant fix cause its says requires superuser previlege..........can i just remove the pdkg and re installing it again from scrath ???

i'll be happy when flash is running.....i spend like 2 days on it so far.....i still think that i can make it hehehe.......

Gprok

---

