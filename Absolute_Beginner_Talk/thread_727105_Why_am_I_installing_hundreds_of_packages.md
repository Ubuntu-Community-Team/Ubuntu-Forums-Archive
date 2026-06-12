---
title: "Why am I installing hundreds of packages??"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by M3lvn on 2008-03-17
Hi, 
I am a super newbie at Ubuntu. 

Im trying to install an nvidia driver for a 8800m gts. 

Im trying to install it via Envy. Envy cant install it bcoz of some error. The error log gives a list of all sorts of dependency packages. I've been installing packages for hours now. Is this normal?!

---

### Post by justin whitaker on 2008-03-17
> **M3lvn said:**
> Hi, 
I am a super newbie at Ubuntu. 

Im trying to install an nvidia driver for a 8800m gts. 

Im trying to install it via Envy. Envy cant install it bcoz of some error. The error log gives a list of all sorts of dependency packages. I've been installing packages for hours now. Is this normal?!

Doesn't sound normal. Could you post the errors?

---

### Post by weezy8802 on 2008-03-17
Make sure your system is up to date and then try to install driver again.

---

### Post by M3lvn on 2008-03-17
Thank you for the quick replies (Im a bit frustrated now, so excuse me svp).

Btw, its a fresh install. 

The error is: 
```

python pulse.py nvidia latest 
root@p6831fx:/usr/share/envy# python pulse.py nvidia latest
Envy - Version 0.9.10
Ubuntu Gutsy 64bit

OK: All the packages are installed
Checking the Dependencies for the New Method
ENVY: 
The following packages are not installed:


libqt3-mt-dev
kernel-wedge

rpm
sharutils

libgtk2.0-dev

libxxf86misc-dev

libxtst-dev

libxxf86vm-dev

libxinerama-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt3-mt-dev
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

```

---

### Post by justin whitaker on 2008-03-17
Given that error, there should not be 100s of packages. Did you run an update on that fresh install before trying to run envy?

---

### Post by Therion on 2008-03-17
I strongly suggest that you do all your system updates -- ALL of them -- *then* use the latest version of Envy to install your driver.

---

### Post by Oldsoldier2003 on 2008-03-17
> **Therion said:**
> I strongly suggest that you do all your system updates -- ALL of them -- *then* use the latest version of Envy to install your driver.

+1 a fresh install has around 198 updates... on gutsy, a fresh install of hardy is close to 400

---

### Post by Nythain on 2008-03-17
or... you could google how to manually install your drivers (nvidia is easy, nto sure about ati) and not install 100's of packages just to have a pretty gui to do it for you...

with nvidia its as easy as downloading the latest driver .run package...
then control+alt+f2
login with your info
sudo /etc/init.d/gdm stop (or kdm for kde users)
cd to directory containing the .run
make sure its executable (wich i actually didnt have to do)
sudo chmod a+x NVIDIA-whatever.run
then run that puppy
sudo sh NVIDIA-whatever.run
follow directions, answer a few yes questions and hope all goes well... it might complain about source or headers, in wich case
sudo aptitude install `uname -r`-headers
or a similar line, will install the linux kernel headers that the package needs to build a module...

also if they are installed, you might have to remove nvidia-glx (or glx-new) and nvidia-kernel-common (not sure but i removed it anyways) and any restricted drivers packages that apt-get/aptitude will want to remove along with those before installing the new drivers :(

thats pretty much what 100's of packages and a pretty gui will do for you, but its really not that complicated

---

### Post by Hospadar on 2008-03-17
It's really better to use the repository version rather than the nvidia download, not only does the nvidia download not work for everyone, but it can be tricky to remove and update.  You should run system updates anyways, even though there are a lot of them.  They provide a lot of security and stability fixes.

---

### Post by Therion on 2008-03-17
> **Nythain said:**
> or... you could google how to manually install your drivers ... and not install 100's of packages just to have a pretty gui ...
Ummmmm...  It's not Envy requiring hundreds of packages to satisfy dependencies; it's a fresh install of Gutsy.

> **Oldsoldier2003 said:**
> +1 a fresh install has around 198 updates... on gutsy, a fresh install of hardy is close to 400
So I discovered about a week ago.  367(!!) to be exact... If memory serves.

---

### Post by justin whitaker on 2008-03-17
> **Therion said:**
> Ummmmm...  It's not Envy requiring hundreds of packages to satisfy dependencies; it's a fresh install of Gutsy.


So I discovered about a week ago.  367(!!) to be exact... If memory serves.

Just wait until you get to Hardy...hehe. :)

---

### Post by Oldsoldier2003 on 2008-03-17
> **justin whitaker said:**
> Just wait until you get to Hardy...hehe. :)

that was hardy! (alpha 6)l

---

### Post by forrestcupp on 2008-03-17
In order for Envy to find dependencies, you have to have the Proposed and Backports repos enabled.

Go to System->Administration->Software Sources and click the Updates tab.  Check the boxes next to 'Pre-released updates' and 'Unsupported updates'.  Then close and type:
```
sudo apt-get update
```

Then you will be able to run Envy.

---

### Post by Nythain on 2008-03-17
A. As far as im concerned, envy should be a last ditch effort... granted, its not got "hundreds" of dependencies, but the ones it does have muck up kde systems... i really dont like needing gksu on a pure kde machine, along with a bunch of gtk libraries and glade stuff... Not to mention the fact, that as far as i could tell, i couldnt run it cli... i believe after the fact, i found out there was a way to run it cli, but i still couldnt run it, because i refuse to slap gksu on my system when i already have sudo and kdesu... if it was better designed to require fewer dependencies to do its job, and considered alternative desktop environments and window managers i would be more apt to suggest it...

B. Its not necessarily better at the moment to run the repo drivers... at least not with a newer card and any repo gutsy or older... i was an avid fan of the repo drivers till i found out how many bugs they had vs. the new drivers... everything from distance clipping in wow, to allowing me to run dual monitors period... with repo drivers, second monitor (if i could get it to work) was forced 640x480... solution i found, was to update drivers, now im runnin double 1600x1200 like i should be

C. im still insisting if its at least nvidia drivers you are dealing with... its easy enough to manual install them without the need of Envy... But i will warn at this point since i havent yet...

If you use Envy, or the manual method, to install drivers not in the repo... your system will break upon updating/upgrading your kernel... its nothing major, you will  just need to reinstall the driver module for that kernel, either through envy, or the manual way... so dont freak out when you upgrade your system, and notice you cant get back into Gnome/KDE/whatever...

---

