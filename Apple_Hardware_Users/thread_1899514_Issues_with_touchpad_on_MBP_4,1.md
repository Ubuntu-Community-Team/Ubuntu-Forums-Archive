---
title: "Issues with touchpad on MBP 4,1"
date: 2011-12-23
forum: Apple Hardware Users
---

### Post by razaz03 on 2011-12-23
Hi all,

Installing Xubuntu 11.10 x64 on my mac book pro (4,1), I'm having trouble with the touchpad after a few mins of usage - it totally locks up sometimes or sometimes I can click/use the keyboard.

It seems as if the touchpad is constantly pressed at times and keyboard locking up when that does.. generally it's super erratic once it bugs out after a few mins.

[https://wiki.ubuntu.com/MacBookPro4-1/Maverick](https://wiki.ubuntu.com/MacBookPro4-1/Maverick) Looking over this the PPA is only showing 3 packages for me with package manager, with only one installed: xserver-xorg-input-synaptics (other two are dev docs and i386 package).
> And verify that the mactel repository was added, then select by origin  and choose mactel, then select all pertainent upgrades, in particular  applesmc.
Can't see applesmc at all. Unable to install it via sudo apt-get install applesmc either, nor any packages as seen in the PPA [https://launchpad.net/~mactel-support/+archive/ppa]("https://launchpad.net/%7Emactel-support/+archive/ppa") here.

Can someone tell me if I'm doing something stupid here? Totally new to macs and just got a macbook pro. I understand that in both the guide (former link) and PPA details (latter link) it's showing support for MBPs 4,1 for older distros.. Perhaps my installing 11.10 is the issue? If so do you recommend reinstalling with 10.10?

Xubuntu 11.10 x64 ,MacBookPro 4,1, Tri-booting

Cheers,

raz

---

### Post by razaz03 on 2011-12-24
Nobody? :(

Essentially just wanna know if the Mactel pages showing support for 10.10 means that the MBP 4,1 is only supported with ubuntu 10.10, with 11.10 being a bad idea!

Cheers



EDIT: OK! Making a new thread with this very general question!

---

### Post by Apewall on 2011-12-25
> **razaz03 said:**
> Nobody? :(

Essentially just wanna know if the Mactel pages showing support for 10.10 means that the MBP 4,1 is only supported with ubuntu 10.10, with 11.10 being a bad idea!

Cheers



EDIT: OK! Making a new thread with this very general question!

On a Macbook Pro 4,1 right now, the issue is that on Xubuntu(not ubuntu) the disable touchpad while typing function does not work.  

However, the mactel ppa has not been updated for 11.10, though many parts of it seem to be now included anyway.

If you installed the xserver-xorg-input-synaptics package from the mactel ppa, REMOVE IT, it is bugged and causes the issues you are describing, the package in ubuntu's default repositories functions much better.

I also had to swap the multitouch functions
as 2 finger click was causing a middle mouse click, and 3 finger click was causing a right click, only occured on xubuntu not ubuntu.

---

### Post by razaz03 on 2011-12-25
> **Apewall said:**
> On a Macbook Pro 4,1 right now, the issue is that on Xubuntu(not ubuntu) the disable touchpad while typing function does not work.  

However, the mactel ppa has not been updated for 11.10, though many parts of it seem to be now included anyway.

If you installed the xserver-xorg-input-synaptics package from the mactel ppa, REMOVE IT, it is bugged and causes the issues you are describing, the package in ubuntu's default repositories functions much better.

I also had to swap the multitouch functions
as 2 finger click was causing a middle mouse click, and 3 finger click was causing a right click, only occured on xubuntu not ubuntu.

Hi! Thanks a lot for the info.

So you didn't install any other packages from the Mactel Support PPA? My problem is I can't even see any to install, yet you say "many parts of them seem to be included now anyway". 

How do I install the other parts? xserver-xorg-input-synaptics was installed by default, and only two other Mactel packages are showing from the Mactel PPA in synaptic (both useless). 

Which others do you recommend for a streamlined experience? I do notice my MBP getting hot (before it crashes) and was wondering whetherI'm doing something stupid in regards to not being able to install other Mactel packages.

Cheers

---

### Post by razaz03 on 2011-12-25
> **Apewall said:**
> 
I also had to swap the multitouch functions
as 2 finger click was causing a middle mouse click, and 3 finger click was causing a right click, only occured on xubuntu not ubuntu.

Totally the same issue with me, how do I swap the functions?


raz

---

### Post by Apewall on 2011-12-25
> **razaz03 said:**
> Totally the same issue with me, how do I swap the functions?


raz

```

sudo nano /usr/share/X11/xorg.conf.d/50-synaptics.conf

```

```


Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        Option "TapButton1" "1"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "FingerHigh" "50"
        Option "Palmdetect" "on"
EndSection


```

TapButton can be used to rebind the functions of the touchpad.

---

### Post by razaz03 on 2011-12-25
> **Apewall said:**
> ```

sudo nano /usr/share/X11/xorg.conf.d/50-synaptics.conf

``````


Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        Option "TapButton1" "1"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "FingerHigh" "50"
        Option "Palmdetect" "on"
EndSection


```TapButton can be used to rebind the functions of the touchpad.

pasting the first command in a terminal, it leads me to a window with no text at all - am I missing out on something here? uninstalled the previous xorg touchpad package as instructed and haven't installed anything else since.

---

### Post by razaz03 on 2011-12-25
After several crashes after a fresh install I can confirm that xubuntu 11.10 with MBP 4,1 is simply unstable and one to avoid.

Will try ubuntu 10.10 and report back if I've problems with that.

---

### Post by Apewall on 2011-12-25
> **razaz03 said:**
> After several crashes after a fresh install I can confirm that xubuntu 11.10 with MBP 4,1 is simply unstable and one to avoid.

Will try ubuntu 10.10 and report back if I've problems with that.

That's simply not true and misleading.  I have no stability issues and have had no crashes.

I will not say it is more "out of the box" than 10.10 or 11.04, but it is certainly not unstable after correct tweaking.

---

