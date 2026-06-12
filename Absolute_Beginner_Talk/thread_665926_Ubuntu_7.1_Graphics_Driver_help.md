---
title: "Ubuntu 7.1 Graphics Driver help"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by vg2626 on 2008-01-12
Hey, this is my first time using Linux and I just installed Ubuntu 7.1.
I am having trouble installing the driver for my graphics card. I have an NVIDIA Geforce4 MX440 Graphics card. I already downloaded the neccesary driver for it but I can't figure out how to install. Please help. Ive seen Videos of people using Linux and I think its pretty cool and I would hate to go back to using strictly Windows.

---

### Post by vg2626 on 2008-01-12
Can any one help!!!!

---

### Post by Sef on 2008-01-12
Have you gone to System > Administration > Restricted Drivers Management?   I had a similar card and that's how I got the restricted drivers for mine.

Don't bump your thread unless 24 hours have gone by.  This is a volunteer forum, so please have patience in waiting for an answer.  Continued excessive bumping can get you an infraction.

---

### Post by polmir on 2008-01-12
[http://ubuntuforums.org/showthread.php?t=543073]("http://ubuntuforums.org/showthread.php?t=543073")

---

### Post by vg2626 on 2008-01-12
yea i have tried that and i get an error that says

The software source for the package

   nvidia-glx

 is not enabled.

---

### Post by vg2626 on 2008-01-12
> **polmir said:**
> [http://ubuntuforums.org/showthread.php?t=543073]("http://ubuntuforums.org/showthread.php?t=543073")

I am trying this but when I enter the code

sudo dpkg-reconfigure xserver-xorg

then I am asked for my password. Then when I go to enter my password, it won't let me type anything. Do you know how to fix that.

---

### Post by RomeReactor on 2008-01-12
> **vg2626 said:**
> yea i have tried that and i get an error that says

The software source for the package

   nvidia-glx

 is not enabled.

You need to enable the necessary repositories. Have you tried installing anything else, and if so, do you get the same error? please post the output of the following command:
```
cat /etc/apt/sources.list
```

> I am trying this but when I enter the code

sudo dpkg-reconfigure xserver-xorg

then I am asked for my password. Then when I go to enter my password, it won't let me type anything. Do you know how to fix that.

The password doesn't show, but it **is** being registered; it's a security feature.

---

### Post by vg2626 on 2008-01-13
> **RomeReactor said:**
> You need to enable the necessary repositories. Have you tried installing anything else, and if so, do you get the same error? please post the output of the following command:
```
cat /etc/apt/sources.list
```



The password doesn't show, but it **is** being registered; it's a security feature.

ok after I entered that code I got the folowing


victor@victor-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
victor@victor-desktop:~$

---

### Post by Sef on 2008-01-13
Easy way to fix that:

Applications > Add/Remove > Change the upper right box to 'All Available Applications.' > OK

The try reinstalling the restricted drivers: System > Administration > Restricted Drivers Management.

---

### Post by polmir on 2008-01-13
```
 gksudo gedit /etc/apt/sources.list
```
delete all #
from the line with link.
After this operation. Save it.

And after

```
sudo apt-get update
```

---

### Post by vg2626 on 2008-01-13
> **Sef said:**
> Easy way to fix that:

Applications > Add/Remove > Change the upper right box to 'All Available Applications.' > OK

The try reinstalling the restricted drivers: System > Administration > Restricted Drivers Management.

After i go to the upper right box and hit 'All Available Applications' What do I do after that.
Am I supposed to remove something or what.

---

### Post by RomeReactor on 2008-01-13
> **vg2626 said:**
> After i go to the upper right box and hit 'All Available Applications' What do I do after that.
Am I supposed to remove something or what.

No, that will enable the repositories. You can also do it by going to 'System->Administration->Software Sources' and checking the first four boxes in the first tab--Ubuntu Software--except for "Source" and "CD-ROM"; then press the "Reload" button when prompted, close that window and go again to 'System->Administration->Restricted Drivers Manager' to enable the drivers there.

---

### Post by vg2626 on 2008-01-13
> **polmir said:**
> ```
 gksudo gedit /etc/apt/sources.list
```
delete all #
from the line with link.
After this operation. Save it.

And after

```
sudo apt-get update
```

so if I understood correctly. You want me to delete all the lines that had a link in it?
and then save. But leave the other lines that didn't have a link.

---

### Post by markusf21 on 2008-01-13
no he wants you to delete the # symbol in those lines

---

### Post by RomeReactor on 2008-01-13
> **vg2626 said:**
> so if I understood correctly. You want me to delete all the lines that had a link in it?
and then save. But leave the other lines that didn't have a link.

Try the GUI method posted by Sef.

---

### Post by vg2626 on 2008-01-13
> **RomeReactor said:**
> No, that will enable the repositories. You can also do it by going to 'System->Administration->Software Sources' and checking the first four boxes in the first tab--Ubuntu Software--except for "Source" and "CD-ROM"; then press the "Reload" button when prompted, close that window and go again to 'System->Administration->Restricted Drivers Manager' to enable the drivers there.

OMG you are a genius this worked and now i have to restart my computer to see if my graphics card is working. I'll be back in a moment. THANKS

---

### Post by vg2626 on 2008-01-13
> **polmir said:**
> ```
 gksudo gedit /etc/apt/sources.list
```
delete all #
from the line with link.
After this operation. Save it.

And after

```
sudo apt-get update
```

Ok, after doing this process. the updates are now finished. Thanks.

---

### Post by vg2626 on 2008-01-13
> **RomeReactor said:**
> No, that will enable the repositories. You can also do it by going to 'System->Administration->Software Sources' and checking the first four boxes in the first tab--Ubuntu Software--except for "Source" and "CD-ROM"; then press the "Reload" button when prompted, close that window and go again to 'System->Administration->Restricted Drivers Manager' to enable the drivers there.

Ok after restarting my system. Everything is now working thank you so much. Now I am going to try to install  beryl 0.2.1

---

### Post by bumanie on 2008-01-13
Beryl is no longer supported. It has been 'fused' with the compiz project. Desktop effects are now known as compiz fusion. You should use that rather than beryl.

---

### Post by vg2626 on 2008-01-13
> **bumanie said:**
> Beryl is no longer supported. It has been 'fused' with the compiz project. Desktop effects are now known as compiz fusion. You should use that rather than beryl.

ok thanks I didn't know that where do I get that and is it an easy install

---

### Post by sneakyzor on 2008-01-13
it comes ubuntu 7.10, you just need to enable it.

goto system > preferences > appearance and enable theme effects

---

### Post by vg2626 on 2008-01-13
> **sneakyzor said:**
> it comes ubuntu 7.10, you just need to enable it.

goto system > preferences > appearance and enable theme effects

I already have the extra effects selected how would you get that cube view and other effects to work.

---

### Post by vg2626 on 2008-01-13
when ever I run 

sudo apt-get update

I get this at the end how do I fix this

Fetched 6B in 7s (1B/s)                                                        
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I also get 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

whenever i run the install code

sudo apt-get install compiz compizconfig-settings-manager

---

### Post by RomeReactor on 2008-01-13
> **vg2626 said:**
> when ever I run 

sudo apt-get update

I get this at the end how do I fix this

Fetched 6B in 7s (1B/s)                                                        
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

whenever i run the install code

sudo apt-get install compiz compizconfig-settings-manager

That usually happens when **Update Manager** is working in the background fetching updates; it's a process that takes two to five of minutes on a broadband connection, so wait until it finishes before you try installing something. Otherwise, make sure you don't have more than one package management program open at the same time, such as Synaptic or Add/Remove, or either of these two when trying to install something from the terminal--as the code above.

---

