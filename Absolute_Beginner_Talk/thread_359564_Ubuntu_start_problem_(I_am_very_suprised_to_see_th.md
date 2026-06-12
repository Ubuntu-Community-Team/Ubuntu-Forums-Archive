---
title: "Ubuntu start problem (I am very suprised to see this)"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-02-12
Hi,
If anyone can help with this  i would be grateful
cant get ubuntu generic to start properly!!!!!!!!!!

I tried to format everything and install ubuntu again fresh
i figured out that when u first install it after intallation finishes
i remove cd and boot normaly for the first time in generic mode
now if try to restartt again then i canot login normally ever after through generic mode
(always loading normally session, entering username, pass and then start up screen and 
the only thing visible is ubuntu background, no taskbars , cursor moves, no right click)
Note this happens always after different format and installation attempts

The only think that you can do is to reboot, login with recovery mode , everything works fine there, and then ctrl Alt Backspace, Exit . So i get to the session login screen and then if i enter again the Username etc it  logs in normally (generic inviroment)
So basically i can only log in generic if i first login recovery, logout and then login normally again

This cant bee right, something stupid is going on
I mean why  the first time after installation i can login normally and then after that i cant?

Many thanks for trying to help

---

### Post by frodon on 2007-02-12
Well the generic kernel is used to launch other kernel than the i386 so i guess that if you didn't installed other kernel it points to nothing.
I guess that you have no problem booting the i386 kernel, right ?

My first question is did you install a specific kernel like i686, k7, ... ?
If not, boot your i386 kernel and install the one you need and try again the generic kernel.

---

### Post by evkefalas on 2007-02-12
Thanks For the reply
the iso i burned and installed is ubuntu-6.10-desktop-i386
The kernel version if i am not mistaken is 6.10.17
The laptop has an Intel Pentium 2.8 GHz on it

(In previous attempts when i ve made the updates as well before rebboting for the first time, i even had the latest kernel 6.10.19 but even that one didnt work!

Any ideas
Thanks a lot for yr help
:)

---

### Post by frodon on 2007-02-12
But why do you want to boot the generic kernel if you didn't install other kernels ?

Just tell me if you don't understand the sense of my question and confirm me if you are able to boot the i386 kernel.

I saw that you have a pentium 2, if it supports hyperthreading or if it is a dual core then install the 686-smp kernel :
```
sudo apt-get install linux-686-smp
```Otherwise intall the standard 686 kernel :
```
sudo apt-get install linux-686
```

Once your specific kernel installed you can try again to boot your generic kernel.

---

### Post by evkefalas on 2007-02-12
I understand now what i have to do
sorry i am complete new to linux
As soon as i go back home after work, i ll install the kernel and then boot again from the generic
Then i ll come and post the result
thanks a lot for the help
:)

---

### Post by evkefalas on 2007-02-13
I tried 
sudo apt-get install linux-686
and when i boot and try to start the 686 kernel i get a screen saying
kernel panic and ubuntu doesnt boot
:(
any ideas?
thanks

---

### Post by evkefalas on 2007-02-13
My system is intel pentium 4 2.8 GHz (no dual or HP)
and has an ATI RADEON 9600 
i read that there are a lot of issues with ati cards and linux
could it be the graphics card creating an issue?

---

### Post by frodon on 2007-02-13
Hum, it's a hard one, do you think you would be able to provide some log or additional information which could help us to find the problem ?

---

### Post by evkefalas on 2007-02-13
of course 
if you tell me how to retrieve it
cause i am completely new to linux 
and chose ubuntu as the most user friendly to begin with :)
thanx for the help

---

### Post by frodon on 2007-02-13
At what step of the boot process do you get the kernel panic ?

---

### Post by evkefalas on 2007-02-13
when i select the 686 kenrnel
press enter
and its the next screen
coming up immediately

---

### Post by frodon on 2007-02-13
No log at all really, even in recovery mode ?

---

### Post by igknighted on 2007-02-13
The generic kernel is the one you should be using.  Edgy went away from the 686/k7/etc kernels and provided one all inclusive one.  You might be having graphics card issues, so try booting into the generic kernel, recovery mode, and typing these commands:
```
apt-get update
apt-get install xorg-driver-fglrx
aticonfig --initial
```

Then reboot and you should be good to go.

---

### Post by evkefalas on 2007-02-13
i havent tried the 686 recovery mode, 
i suspected the graphics card too
i ll give it a try in a hour when i am back home
thanx for the help

---

### Post by evkefalas on 2007-02-13
tried it and get the following

evan@evan-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
evan@evan-laptop:~$ apt-get install xorg-driver-fglrx
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
evan@evan-laptop:~$ aticonfig --initial
evan@evan-laptop:~$

---

### Post by shareMenaPeace on 2007-02-13
> **evkefalas said:**
> tried it and get the following

evan@evan-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
evan@evan-laptop:~$ apt-get install xorg-driver-fglrx
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
evan@evan-laptop:~$ aticonfig --initial
evan@evan-laptop:~$

Put a sudo infrotn of the commands to run them with admin privileges. As these steps need this. You need to type in your password aswell.
```

sudo apt-get update
```

etc

---

### Post by evkefalas on 2007-02-13
ok i run the commands fine

i got:

evan@evan-laptop:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
evan@evan-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
The following packages were automatically installed and are no longer required:
  cramfsprogs kernel-headers-2.4.27-2 initrd-tools
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 130 not upgraded.
evan@evan-laptop:~$ aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
evan@evan-laptop:~$

---

### Post by evkefalas on 2007-02-13
Yet problem not resolved
still cant boot from the generic normally

---

### Post by evkefalas on 2007-02-14
After trying all the above, i cant boot normally into the generic mode
:(

---

### Post by evkefalas on 2007-02-16
I am pretty convinced that the issue is drivers for my ATI 9600
I ve tried a lot of stuff and including both methods described here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) 

But at no point i could get the 3d accelaration working and the drivers correctly for the card
CAn anyone please Help

---

### Post by evkefalas on 2007-02-16
installed again drivers
fglrxinfo output:

evan@evan-laptop:~$ fglrxinfo
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

### Post by evkefalas on 2007-02-16
Finally it starts properly
 but no direct rendering
evan@evan-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
evan@evan-laptop:~$ 


What should i do????
Thanks

---

### Post by evkefalas on 2007-02-16
I quess since no one can help with this issue
 and i am unexperienced user,
i will have to drop ubuntu
since i can not make it work properly on my computer

i am very surprised to see all these problems with the ati cards
and drivers
so that it is prohibited to use the platform
ATi is a very well distributed graphics brand
so in my opinion support on this should have been better
i ve tried a million posts and different installations
format after format and everytime the same
its a pitty
farewell ubuntu
thanks

---

### Post by evkefalas on 2007-02-16
ps after all this effort 
after the first boot, ubuntu canot boot properly again
only boot  recovery first 
logout
exit
then login again
to get to generic normal view
Its 100% drivers issue

---

### Post by evkefalas on 2007-02-18
installed kubuntu and everything works fine
no extra drivers needed
even beryl works fine
no problems whatsoever
amazing

---

