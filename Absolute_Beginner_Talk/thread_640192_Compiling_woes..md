---
title: "Compiling woes."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by YodaMstr on 2007-12-13
So, Ubuntu is going to be my first Linux distro experience.  As such, I have no clue how much of it works.  I plan on fixing that once I can get in and play around with it, but for now I'm stuck.

I may be able to find it somewhere in the support, but I figured I'd ask here to get a quicker, more precise answer.

Anyways, compiling.  My wireless card isn't supported out of the "box", so I downloaded ndiswrapper-1.50.tar.  Went into Ubuntu, unpacked it, and....couldn't figure out how to proceed from there.  Any help?

---

### Post by spiderbatdad on 2007-12-13
ndiswrapper is in synaptic package manager. much better to get it from there, but your still going to need drivers, and probably wpa supplicant (also in synaptic). Are you positive your card wont work without ndiswrapper? I would consider it a last resort. also maybe this will help:
[http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless)

---

### Post by spiderbatdad on 2007-12-13
you'll want:
ndiswrapper-common, ndiswrapper-utils-1.9, and i see an interesting looking GUI (ndisgtk) if you enable all the sources....System--Administration--Software Sources...check all but source code.

---

### Post by YodaMstr on 2007-12-13
It's a 1390 WLAN Mini-card that I have.  I checked this link right [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell") and it said that the card isn't supported.

And it's alright if it's a last resort.  I just have to get wireless working so I can work directly off Ubuntu, and then I can work on setting it up properly.

---

### Post by RomeReactor on 2007-12-13
Hi. If internet access in your Ubuntu system is out of the question--even a wired connection--then the easiest way to install NdisWrapper is to download the following .deb packages:

* [ndiswrapper-common]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb")

* [ndiswrapper-utils]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb")

* [ndisgtk]("http://mirrors.xmission.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb")

The packages are for Ubuntu 7.10 Gutsy Gibbon 32 bit. Once you have them on your Ubuntu system, double click on each to install them, in the order listed above. Once installed, you'll find the graphical interface in "System->Administraion->Windows Wireless Drivers".

And welcome to the community!

---

### Post by YodaMstr on 2007-12-13
Alright, thank you very much.  I'll get to work on that right now!  I should be back shortly with an answer.

Hoping to figure all this out soon.  It's a bit overwhelming, to be honest.  Probably because I need to be on the interface as I'm reading through the help files. =P  But anyways, thanks!  Wish me luck!

---

### Post by spiderbatdad on 2007-12-13
@RomeReactor +1

---

### Post by YodaMstr on 2007-12-16
Wow...I really have no clue what I'm doing.  I get to the graphical interface and it shows that no windows drivers are installed.  It allows me to add them, but I have no clue WHERE I'm supposed to add them from.  Sorry to be such a bother with this.

---

### Post by RomeReactor on 2007-12-16
If you have the CD that came with your wireless card, there should be a folder with drivers on it; look for files ending in **.INF** and **.SYS**. You need to use NdisGTK to navigate to that **.INF** file.

---

### Post by YodaMstr on 2007-12-16
I'm sorry to be such a bother.

All the .inf files I could find on this driver CD were invalid or the hardware wasn't present.  I found the .exe for the driver on the Dell website, so would it be possible to run that in Windows and pull the driver from the files afterwards?

---

### Post by RomeReactor on 2007-12-16
For your card, I think you need to blacklist the **bdm43xx** driver included in Ubuntu:
```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```

You can extract the necessary .INF and .SYS files from that .EXE; to make things easier, move your .EXE file to your home folder, but don't put it in any sub-directory. Now open a terminal, and enter:
```
unzip -a R151517.EXE
```

This will extract a folder--let's say the name is **DRIVER**--and then you must enter that folder from the terminal:
```
cd DRIVER
```

and to install the drivers:
```
sudo ndiswrapper -i bcmwl5.inf
```

More information on that [in this thread]("http://ubuntuforums.org/showthread.php?t=297092"); read from **STEP 4: INSTALL DRIVERS**.
 Just note that this guide uses the terminal instead of the graphical NdisGTK application.
Hope this helps.

---

