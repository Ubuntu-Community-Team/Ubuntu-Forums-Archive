---
title: "at my wits end with ubuntu"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by kansaibear on 2006-09-13
trying to install synaptics-0.14.6 because my cursor jumps all over while I am trying to type...why the hell isnt there a touchpad setting with the mouse  settings....

anyway, the instructioins start...
Installing
----------

1. Type "make" to build the driver "synaptics_drv.o".

######### just where am I supposed to type "make" ??

2. Copy the driver module "synaptics_drv.o" into the XFree module
   path. This path is usually "/usr/X11R6/lib/modules/input/", and
   running "make install" as root will do this for you. Note though
   that some distributions have a different module path. For example,
   in Gentoo 1.4 (with XFree86 4.3.0), the correct path is
   "/usr/X11R6/lib/modules/drivers".

3. Add the driver to the XFree configuration file (usually called
   /etc/X11/XF86Config-4 or /etc/X11/XF86Config)

########## what is the difference between the driver module and the driver??

someone want to translate that for me?
here is how I started... surely I look like an idiot but here is my terminal:
bear@ubuntu:~$ sudo /home/ make
Password:
sudo: /home/: command not found
bear@ubuntu:~$ sudo /home/synaptics-0.14.6 make
sudo: /home/synaptics-0.14.6: command not found
bear@ubuntu:~$ sudo make /home/synaptics-0.14.6
sudo: make: command not found
bear@ubuntu:~$ sudo make
sudo: make: command not found
bear@ubuntu:~$ cd /home/
bear@ubuntu:/home$ sudo make
sudo: make: command not found
bear@ubuntu:/home$ cd /home/synaptics-0.14.6
bash: cd: /home/synaptics-0.14.6: No such file or directory
bear@ubuntu:/home$ cd /home/synaptics-0.14.6/
bash: cd: /home/synaptics-0.14.6/: No such file or directory
bear@ubuntu:/home$

Can someone give me a heads up here before I throw my powerbook thru the window??

---

### Post by Crayoneater on 2006-09-13
you are trying to build from source, so you need to install the build-essential package..type: sudo apt-get install build-essential

after that, you will need to cd into the synaptics-0.14.6 directory (wherever downloaded it to) and then type: make

after it is done (with no errors hopefully) you should type: sudo make install

the step three in the installation instructions is telling you to edit  the xorg.conf file but i'm not sure how to edit it....

an easier way to install the synaptics driver would be to install it using apt-get, although you need to have the correct repositories i believe...all i have to do to install it is type: sudo apt-get install xfree86-driver-synaptics

i can also install qsynaptics or tpconfig to configure the touchpad settings: sudo apt-get install tpconfig qsynaptics

---

### Post by Kilz on 2006-09-13
> **kansaibear said:**
> trying to install synaptics-0.14.6 because my cursor jumps all over while I am trying to type...why the hell isnt there a touchpad setting with the mouse  settings....

anyway, the instructioins start...
Installing
----------

1. Type "make" to build the driver "synaptics_drv.o".

######### just where am I supposed to type "make" ??

2. Copy the driver module "synaptics_drv.o" into the XFree module
   path. This path is usually "/usr/X11R6/lib/modules/input/", and
   running "make install" as root will do this for you. Note though
   that some distributions have a different module path. For example,
   in Gentoo 1.4 (with XFree86 4.3.0), the correct path is
   "/usr/X11R6/lib/modules/drivers".

3. Add the driver to the XFree configuration file (usually called
   /etc/X11/XF86Config-4 or /etc/X11/XF86Config)

########## what is the difference between the driver module and the driver??

someone want to translate that for me?
here is how I started... surely I look like an idiot but here is my terminal:
bear@ubuntu:~$ sudo /home/ make
Password:
sudo: /home/: command not found
bear@ubuntu:~$ sudo /home/synaptics-0.14.6 make
sudo: /home/synaptics-0.14.6: command not found
bear@ubuntu:~$ sudo make /home/synaptics-0.14.6
sudo: make: command not found
bear@ubuntu:~$ sudo make
sudo: make: command not found
bear@ubuntu:~$ cd /home/
bear@ubuntu:/home$ sudo make
sudo: make: command not found
bear@ubuntu:/home$ cd /home/synaptics-0.14.6
bash: cd: /home/synaptics-0.14.6: No such file or directory
bear@ubuntu:/home$ cd /home/synaptics-0.14.6/
bash: cd: /home/synaptics-0.14.6/: No such file or directory
bear@ubuntu:/home$

Can someone give me a heads up here before I throw my powerbook thru the window??

First make sure that the Universe repository is enabled, if your not sure [go here to read how to do it.]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")
Sure, Click System > Adminastration > Synaptic Packkage Manager
Type in your password
Click search
type in synaptics
Click on the box by the package thats already built for your system to install it.

---

### Post by 3rr0r on 2006-09-13
You can edit the file using
```
 sudo nano filename
```
or
```
sudo gedit filename
```

or if you prefer a graphical interface
```
gksudo gedit filename
```

Good luck

---

### Post by theboomboomcars on 2006-09-13
If you are trying to turn of the tapping feature I don't think you have to install a new driver.  I didn't.  Here is what the synaptics portion of my xorg.conf:
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
EndSection
The MaxTapTime is the tapping.  Check your xorg.conf file to see if it has the synaptics section already, if it does you don't need to install a new driver.
Hopefully you can get it to cooperate, I know how annoying it is to be typing and then suddenly your cursor is somewhere else.

---

### Post by 3rr0r on 2006-09-13
> **theboomboomcars said:**
> If you are trying to turn of the tapping feature I don't think you have to install a new driver.  I didn't.  Here is what the synaptics portion of my xorg.conf:
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
EndSection
The MaxTapTime is the tapping.  Check your xorg.conf file to see if it has the synaptics section already, if it does you don't need to install a new driver.
Hopefully you can get it to cooperate, I know how annoying it is to be typing and then suddenly your cursor is somewhere else.

can you tell me the full path to get to the xorg.conf file? Thanks!

---

### Post by eylisian on 2006-09-13
It's in /etc/X11/xorg.conf but you can always cheat and run locate.```
locate xorg.conf
```

I did a aptitude search and it came up with some synaptics results;
```
xserver-xorg-input-synaptics
```
Being among them. There is also a KDE app to help with configuration, maybe that will help in the future.

peas.

---

### Post by theboomboomcars on 2006-09-13
> **3rr0r said:**
> can you tell me the full path to get to the xorg.conf file? Thanks!

/etc/X11/xorg.conf
the capital X is important since linux is case sensitive.

---

### Post by kansaibear on 2006-09-13
well.... I did indeed edit the xorg.conf file and checked to make sure it was saved... didnt stop the infernal touchpad jig so I thought I needed a newer version.

Tried synaptics and updated the repositories but I am getting several error messages about different repositories that are not configured properly... I have not had much luck with synaptics, keeps coming back 'no file found'. I wanted to down load sunbird calendar but it cant seem to find it and I screwed something up when I downloaded it from mozilla. For now the touch pad is priority. Right now I am typing on my OSX powerbook so I dont go insane....

By the way, I installed 5.10

I did get the build essential installed but I got errors when I ran make... and if I run install, will it install where it is supposed to??

I figure with the time I have in this already I could have bought a used powerbook and loaded it up with Tiger... 

Anway, looking for some more suggestions... Thanks!!

---

### Post by Kilz on 2006-09-13
> **kansaibear said:**
> well.... I did indeed edit the xorg.conf file and checked to make sure it was saved... didnt stop the infernal touchpad jig so I thought I needed a newer version.

Tried synaptics and updated the repositories but I am getting several error messages about different repositories that are not configured properly... I have not had much luck with synaptics, keeps coming back 'no file found'. I wanted to down load sunbird calendar but it cant seem to find it and I screwed something up when I downloaded it from mozilla. For now the touch pad is priority. Right now I am typing on my OSX powerbook so I dont go insane....

By the way, I installed 5.10

I did get the build essential installed but I got errors when I ran make... and if I run install, will it install where it is supposed to??

I figure with the time I have in this already I could have bought a used powerbook and loaded it up with Tiger... 

Anway, looking for some more suggestions... Thanks!!


I honestly suggest to download Dapper and install it.

---

### Post by omns on 2006-09-13
.

---

### Post by kansaibear on 2006-09-14
wwhat I try here I am meeting with defeat. I nt seem to get past the synaptic driver install so l I would give a try to upgrade to dapper  . A bit worried about that cause the old girl his is an old world wallstreet and the original install was a little problematic. 

Anyway, tried various upgrades including upgrade manager but... seems that there is a problem with respositories. Tried to see about fixin that but...

I get this when I edited the repositories... 
your computer has the following problems...

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/universe Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/multiverse Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)
here is what I get when I just try a simple upgrade:

bear@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/universe Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/multiverse Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
bear@ubuntu:~$

well duh.... cant run apt-get update but it tells me to... 

Sisyphus lives....

---

### Post by omns on 2006-09-14
.

---

