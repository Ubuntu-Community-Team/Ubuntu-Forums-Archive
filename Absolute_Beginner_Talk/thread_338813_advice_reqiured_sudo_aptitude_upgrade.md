---
title: "advice reqiured sudo aptitude upgrade"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-01-15
I have pending updates (16). I run update and then upgrade and this is the terminal response;

tony@tony:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  xserver-xorg-dev 
The following packages have been automatically kept back:
  beryl 
The following packages have been kept back:
  beryl-settings-bindings 
The following packages will be upgraded:
  beryl-core beryl-plugins beryl-plugins-data beryl-settings emerald 
  libberylsettings0 libemeraldengine0 
  linux-restricted-modules-2.6.17-10-generic mozilla-mplayer wpasupplicant 
10 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 12.7MB of archives. After unpacking 3155kB will be freed.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  beryl-core libberylsettings0 beryl-settings beryl-plugins wpasupplicant 
  mozilla-mplayer emerald libemeraldengine0 beryl-plugins-data 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": no


What do I do. I answered Yes earlier on today and after the upgrade my system would not startx due to a NVIDIA mismatch. I ran sudo envy and all is now well. Do I risk it again?

tchoklat

---

### Post by bscbrit on 2007-01-15
It depends on which repos you are using.  The warning is simply to say that the downloads cannot be verified for some reason - perhaps they do not contain gpg signatures, perhaps you have a missing item.  If you trust the repos (i.e. they are ALL normal Ubuntu standard repos) then the risk is minimal.  If however you have added to your repos list then there is a risk that one or more of the downloads is not what is says it is and it _could_ run malicious code on your machine.

There is nothing in the download list that should affect your nvidia drivers.

---

