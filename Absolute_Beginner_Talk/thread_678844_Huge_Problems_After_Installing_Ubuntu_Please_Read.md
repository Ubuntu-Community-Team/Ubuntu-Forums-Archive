---
title: "Huge Problems After Installing Ubuntu Please Read"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by godfromdfo on 2008-01-26
i'm typing this on another pc, but here are the problems on my newely installed ubuntu:

for starters it deleted windows or something... after I installed it I checked it then restarted and windows xp was on the list but when I selected it , it wouldnt go on.. I waited like 20 mins and it kept saying starting windows... but if I can get the internet on ubuntu windows doesnt matter..

When I go to try and enable my nvidia card (MX 440) it says Nvidia-glx not enabled please help me on this one... I have no clue

also it wont open exe's? how do I install buffalo Client Manager 3 and the drivers?

---

### Post by mikeyphi on 2008-01-26
> **godfromdfo said:**
> i'm typing this on another pc, but here are the problems on my newely installed ubuntu:

for starters it deleted windows

When I go to try and enable my nvidia card (MX 440) it says Nvidia-glx not enabled please help

also it wont open exe's? how do I instasl buffalo?

For Nvidia First enable the 4 sources under System/Administration/Software Sources
Then open the Restricted Drivers Manager and enable Nvidia

Bad luck about your windows - perhaps you chose 'use entire drive' during the install process?
It might be that windows is still there but not showing on the grub menu
When you get into Ubuntu - post the file    /boot/grub/menu.lst
(that's a small L... not a number1)

It's not possible to open exe in ubuntu - that's a MS format...however, some exe programs will run if installed under Wine - which is available under Add/Remove

---

### Post by godfromdfo on 2008-01-26
Thanks for rplying but I kinda edited the post before you replied =]] also how do I do this? [http://ubuntuforums.org/showthread.php?p=4159357](http://ubuntuforums.org/showthread.php?p=4159357)

EDIT: also I tried to tick the first 4 optiions in the source place but it said I need a internet connection...

---

### Post by rich.bradshaw on 2008-01-26
You need to get some files from the internet first (Yes, It's a bit of a catch 22...), so plug in using an ethernet cable.

Just type the steps into a terminal one by one.

If you are just starting, don't worry about what they do, just get internet working and worry about that later!

Use the bottom guys instructions:

sudo apt-get update
sudo apt-get install ndiswrapper

Then, get the netg125s.inf, usb8023.sys, rndismp.sys files from somewhere, try searching through the cd for windows that comes with the wireless thing for it. Using the file manager, copy them from CD (or wherever you find it) into you Home directory. Then back in a terminal type:

sudo ndiswrapper -i netg125s.inf
sudo cp usb8023.sys rndismp.sys /etc/ndiswrapper/netg125s/
ndiswrapper -l
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
iwconfig

after each sudo command you need to put in your password.

---

### Post by godfromdfo on 2008-01-26
the problem for me is, I kinda cant connect it with a ethernet... because of how far the pc is... and ir's too much to un-wire and all that stuff... so couldnt I download what I need and put it on a disc then transfer it ?

EDIT: also couldnt I do what: [http://ubuntuforums.org/showthread.php?p=4159357](http://ubuntuforums.org/showthread.php?p=4159357) did to connect to the internet?

---

### Post by godfromdfo on 2008-01-26
aloud to bump?

---

### Post by godfromdfo on 2008-01-26
please help me with this I have no clue on how I can get ndiswrapper...

---

### Post by Mr. Eddy on 2008-01-26
Isn't it possible to connect your pc with a wired connection? that would make things a lot easier.

---

### Post by Mr. Eddy on 2008-01-26
if you realy can't connect to the internet, download these files and install them in ubuntu by double clicking on them.

[http://www.opensourcemirrors.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb](http://www.opensourcemirrors.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb)

[http://ubuntu.mirrors.tds.net/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb)

[http://mirror.clarkson.edu/pub/ubuntu/pool/main/g/glibc/libc6_2.5-0ubuntu14_i386.deb](http://mirror.clarkson.edu/pub/ubuntu/pool/main/g/glibc/libc6_2.5-0ubuntu14_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu0.1_i386.deb)

first install libc6 then perl then ndiswrapper-common then ndiswrapper-utils

after that follow:

> **rich.bradshaw said:**
> get the netg125s.inf, usb8023.sys, rndismp.sys files from somewhere, try searching through the cd for windows that comes with the wireless thing for it. Using the file manager, copy them from CD (or wherever you find it) into you Home directory. Then back in a terminal type:

sudo ndiswrapper -i netg125s.inf
sudo cp usb8023.sys rndismp.sys /etc/ndiswrapper/netg125s/
ndiswrapper -l
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
iwconfig

after each sudo command you need to put in your password.

---

### Post by godfromdfo on 2008-01-26
How do I install them? do I click 'run' 'run in terminal' 'cancel' or the other option? I mean what do I do? =\\

---

### Post by Mr. Eddy on 2008-01-26
right click on the file and click on 'open with gdebi'

---

### Post by godfromdfo on 2008-01-26
ioh didnt see the 2nd page... is that all I do right click and install with that? any more steps? if not I will reinstall it

---

### Post by Mr. Eddy on 2008-01-26
otherwise, put the downloaded files in your homedirectory. Start terminal and type:

```
sudo gdebi libc6_2.5-0ubuntu14_i386.deb perl_5.8.8-7ubuntu0.1_i386.deb ndiswrapper-common_1.38-1ubuntu1_all.deb ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
```

hit enter
give password
hit enter

---

### Post by godfromdfo on 2008-01-26
Thank you very much, I will install ubuntu again and hope the internet will work this time, also what would that install? my usb card driver or client manager? or both?

if just the driver can you please explain how I use the internet with it? =\\ because what I used to use on windows was client manager 3 and I just clicked AOSS and it got me on the internet.. lol thanks again

---

### Post by Mr. Eddy on 2008-01-26
reinstalling will not solve the wireless problem, unless you reinstall with a wireconnection. I don't understand your message very well.

did the above work? did you get error?

---

### Post by godfromdfo on 2008-01-26
I will explain, I uninstalled ubuntu to install windows so I can ask why my internet wasnt working on ubuntu (My hard drive don't like dual booting)

---

### Post by mikeyphi on 2008-01-28
So - what's the position now?

---

