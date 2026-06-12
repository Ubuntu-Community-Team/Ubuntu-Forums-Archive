---
title: "Can't install NVIDIA Drivers - &quot;libc&quot; problems"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by nogoodreason on 2008-02-28
Hi guys.

First let me just say that I've been looking forward to using Ubuntu for a long time.  I've finally got around to setting up a dual-boot on my new system and am eager to learn, **but** at this moment in time I know practically nothing... so please speak slowly. ;)

My problem:

I'm trying to install the driver for my nvidia graphics card.  The first time I tried it told me I had to disable 'X Server' before I could continue.  So I did some Googling, typed ```
sudo update-rc.d -f gdm remove
``` and managed to boot Ubuntu without the GUI desktop interface.

I then tried installing the driver again, and was almost successful until I got a message saying:

**Error: You do not appear to have libc header files installed on your system.  Please install your distribution's libc development package.**


...I have absolutely no idea what that means, or what to do.  Um... help?? :(

---

### Post by taurus on 2008-02-28
What nvidia card do you have?  And have you at least looked in System -> Administration -> Restricted Drivers Manager to see if there is a driver for your card?

---

### Post by Medieval_Creations on 2008-02-28
I'm curious, but didn't the live CD isntall Gnome, even though I know it's not running the nvidia drivers yet?

Because even while in being in Gnome you should be able to install the nvidia drivers using the "Restricted Manager"  Which should take care of instlling & setting up you vid card for you.  That's how I setup my nvidia 6800...

as for the libc dependency, I'm not exactly sure which packages to suggest, but I think this should install them.

```
sudo apt-get install build-essentials
```

This installs the basics needed to compile and build apzz from source.

I would give the restricted manager a go first though... may make things easier on you.

---

### Post by glennric on 2008-02-28
First, you don't need to disable the x-server, you need to temporarily stop it.  To do this type
```
sudo /etc/init.d/gdm stop
```
Now that you disabled the x-server with what you did, the x-server will not longer start at boot up.  To renable it type
```
sudo update-rc.d gdm defaults
```
To install the nvidia drivers it is much easier to go to System->Administration->Restricted Drivers Manager and enable the drivers from there.

---

### Post by nogoodreason on 2008-02-28
Thanks for the fast responses!

My card is the **BFG Nvidia 8800GTS 512mb**.  And going into Restricted Drivers Manager was one of the first thing I did, but a message popped up saying something like "no drivers needed" (can't remember the exact wording, but essentially it didn't give me a chance to change anything).

I'll boot back into Linux now and try what's been posted.  :)

---

### Post by anewguy on 2008-02-28
I'm going to assume you have access to the desktop and the net yet.  Look for Envy and try using it to install your drivers.  A LOT of people have used it (it's free) when they couldn't get things to work otherwise.:)

---

### Post by philinux on 2008-02-28
Or use this ENVY.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by nogoodreason on 2008-02-28
When I go into Restricted Drivers Manager I get the message "**Your hardware does not need any restricted drivers."**

I typed ```
sudo /etc/init.d/gdm stop
```
and it took me to a black and white booting screen that seemingly stalled.

Then I tried running ENVY and, well... here's what it says in my terminal:

```
dan@ubuntu:~$ sudo apt-get install -f
[sudo] password for dan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dan@ubuntu:~$ cd \Desktop
dan@ubuntu:~/Desktop$ sudo dpkg -i envy*.deb
Selecting previously deselected package envy.
(Reading database ... 88932 files and directories currently installed.)
Unpacking envy (from envy_0.9.10-0ubuntu4_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
 envy depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy
```

---

### Post by nogoodreason on 2008-02-28
Just noticed that * in the envy title.  Changed it to the exact name of the file and now the Terminal reads:

> dan@ubuntu:~/Desktop$ sudo dpkg -i envy_0.9.10-0ubuntu4_all.deb
(Reading database ... 89336 files and directories currently installed.)
Preparing to replace envy 0.9.10-0ubuntu4 (using envy_0.9.10-0ubuntu4_all.deb) ...
Unpacking replacement envy ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
 envy depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy


---

### Post by Medieval_Creations on 2008-02-28
Run this command first.
```
sudo apt-get install build-essential
```

Then try
```
sudo dpkg -i envy_0.9.10-0ubuntu4_all.deb
```

Should take care of that error anyway.

---

### Post by nogoodreason on 2008-02-28
> **Medieval_Creations said:**
> Run this command first.
```
sudo apt-get install build-essential
```

Then try
```
sudo dpkg -i envy_0.9.10-0ubuntu4_all.deb
```

Should take care of that error anyway.

This is just odd.

Did exactly what you said, but still get all these errors which imply that debhelper, dpatch, libstdc++5 etc are not installed. :(

---

### Post by Medieval_Creations on 2008-02-28
Those packages must not be included in the build-essential meta package.
You can search for those packages either in Synaptic or apt and just install them individually.

Synaptic would be in you menu under Administrator.  ( I don't run Gnome, so I'm fuzzy on the specific location).

If you wanted to try searching with atp the code would be something like this, where ### is a package or program you are looking for.
```
apt-cache search ###
```

You would then get a list that matches ###.

Once you see the package on the list you want, you would run apt-get install again using the full name listed.
```
sudo apt-get install xxx
```

Honestly, Synamptic makes this much easier.

You may have to do this a few more times too.  Depending on what other libraries Envy needs.

---

### Post by nogoodreason on 2008-02-28
> **Medieval_Creations said:**
> as for the libc dependency, I'm not exactly sure which packages to suggest, but I think this should install them.

```
sudo apt-get install build-essentials
```

This installs the basics needed to compile and build apzz from source.


Copied and pasted from Terminal:

[B]dan@ubuntu:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
[/B]

:confused:

---

### Post by taurus on 2008-02-28
> **nogoodreason said:**
> Copied and pasted from Terminal:

**dan@ubuntu:~$ sudo apt-get install build-essential[COLOR="Blue"][B]s**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
[/B]

:confused:

Remove the **[COLOR="Blue"]s[/COLOR]** at the end.

---

### Post by nogoodreason on 2008-02-28
dan@ubuntu:~$ sudo apt-get install debhelper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debhelper has no installation candidate



and if I type **sudo apt-get install build-essential** (without the 's') if says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  fakeroot
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




I really am stumped. :(

---

