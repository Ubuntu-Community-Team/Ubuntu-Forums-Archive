---
title: "Gutsy installed on Gateway Laptop Problems"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by saab on 2007-10-30
I am new to Linux and am having some problems on my Gateway laptop.  If there are any links I should check out, please feel free to point me to them.  I tried searching for a couple of days, but have not been able to find out what I need.

Here is a list of what is going on:
1. I am not getting any sound.  I know this is common on these laptops, but I have not found an easy to follow fix (remember, I am new)

2. I do not know how to set up my Echo Indigo DJ sound card.

3. I tried to install Audacious instead of the stock music player.  I first uninstalled Rhytmbox and tried to install Audacious.  I could not install Audacious because it said that there was a conflicting program already installed, so I tried to just go back to Ryhtmbox, but could not because it told me it was not supported in i386.

4. I can not install the w32codecs.  not sure why.

Any help would be greatly appreciated.
-John

---

### Post by Inxsible on 2007-10-30
> **saab said:**
> I am new to Linux and am having some problems on my Gateway laptop.  If there are any links I should check out, please feel free to point me to them.  I tried searching for a couple of days, but have not been able to find out what I need.

Here is a list of what is going on:
1. I am not getting any sound.  I know this is common on these laptops, but I have not found an easy to follow fix (remember, I am new)

2. I do not know how to set up my Echo Indigo DJ sound card.

3. I tried to install Audacious instead of the stock music player.  I first uninstalled Rhytmbox and tried to install Audacious.  I could not install Audacious because it said that there was a conflicting program already installed, so I tried to just go back to Ryhtmbox, but could not because it told me it was not supported in i386.

4. I can not install the w32codecs.  not sure why.

Any help would be greatly appreciated.
-John

3)```
sudo aptitude install audacious
```

4) Applications --> Add/Remove. Search for "GStreamer" without quotes and install all GStreamer codecs
Also ```
sudo aptitude install w32codecs
```

---

### Post by saab on 2007-10-30
3. I get this:
> john@john-laptop:~$ sudo aptitude install audacious
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  audacious-plugins audacious-plugins-extra qjackctl 
The following NEW packages will be automatically installed:
  jackd ladcca2 libaudacious5 libbinio1c2 libfluidsynth1 libfreebob0 
  libjack0 libjack0.100.0-0 libmcs1 libmms0 libresid-builder0c2a 
  libsidplay2 
The following NEW packages will be installed:
  audacious jackd ladcca2 libaudacious5 libbinio1c2 libfluidsynth1 
  libfreebob0 libjack0 libjack0.100.0-0 libmcs1 libmms0 
  libresid-builder0c2a libsidplay2 
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 4188kB of archives. After unpacking 11.5MB will be used.
The following packages have unmet dependencies:
  qjackctl: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) which is a virtual package.
  audacious-plugins: Depends: libmad0 (>= 0.15.1b) which is a virtual package.
  audacious-plugins-extra: Depends: libartsc0 (>= 1.5.0-1) which is a virtual package.
                           Depends: libmpcdec3 which is a virtual package.
                           Depends: libpulse0 which is a virtual package.
                           Depends: libsamplerate0 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
audacious [Not Installed]
audacious-plugins [Not Installed]
audacious-plugins-extra [Not Installed]
jackd [Not Installed]
libfluidsynth1 [Not Installed]
libjack0 [Not Installed]
libjack0.100.0-0 [Not Installed]
qjackctl [Not Installed]

Score is -9818

Accept this solution? [Y/n/q/?] 


4. On half of the plugins I get this message:> Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

when running the w32codec command I get this:

> john@john-laptop:~$ sudo aptitude install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  w32codecs 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3MB of archives. After unpacking 34.5MB will be used.
The following packages have unmet dependencies:
  w32codecs: Depends: libstdc++5 (>= 1:3.3.4-1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
john@john-laptop:~$ 


any ideas?

Thanks again

---

### Post by Inxsible on 2007-10-30
System --> Administration --> Synaptic Package Manager.

Left hand Navigation Menu, look for Not Installed (Obsolete) or Broken and let us know what packages are listed in there.

---

### Post by Octavgmail.come on 2007-10-30
I have a gateway laptop and had the same issue with no sound, the following worked for me, hope this helps.

open up your volume control go to edit prefs enable external amplifier go back to your volume control go to switches and click the external amplifier off you may need to switch it off then on then off again real quick!

have a cd running with sound so you can tell it works it will be immediate so don't turn up your volume all the way!:)

---

### Post by saab on 2007-10-30
> **Inxsible said:**
> System --> Administration --> Synaptic Package Manager.

Left hand Navigation Menu, look for Not Installed (Obsolete) or Broken and let us know what packages are listed in there.

I do not have a Not Installed (Obsolete), but I have a Not Installed (residual config).  on the right, the only thing listed is Rhythmbox.  if I try and mark it for installation, I get the following message:

> rhythmbox:

Package rhythmbox has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list



---

### Post by Inxsible on 2007-10-30
lets do this again```
sudo aptitude remove rhythmbox
```Doing the above will also remove ubuntu-desktop which is a meta-package so it's not a problem. Then try```
sudo aptitude install audacious
```

---

### Post by saab on 2007-10-30
> **Inxsible said:**
> lets do this again```
sudo aptitude remove rhythmbox
```Doing the above will also remove ubuntu-desktop which is a meta-package so it's not a problem. Then try```
sudo aptitude install audacious
```

Here is what I got.  Same problem:

> john@john-laptop:~$ sudo aptitude remove rhythmbox
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
john@john-laptop:~$ sudo aptitude install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  audacious-plugins audacious-plugins-extra qjackctl 
The following NEW packages will be automatically installed:
  jackd ladcca2 libaudacious5 libbinio1c2 libfluidsynth1 libfreebob0 
  libjack0 libjack0.100.0-0 libmcs1 libmms0 libresid-builder0c2a 
  libsidplay2 
The following NEW packages will be installed:
  audacious jackd ladcca2 libaudacious5 libbinio1c2 libfluidsynth1 
  libfreebob0 libjack0 libjack0.100.0-0 libmcs1 libmms0 
  libresid-builder0c2a libsidplay2 
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 4188kB of archives. After unpacking 11.5MB will be used.
The following packages have unmet dependencies:
  qjackctl: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) which is a virtual package.
  audacious-plugins: Depends: libmad0 (>= 0.15.1b) which is a virtual package.
  audacious-plugins-extra: Depends: libartsc0 (>= 1.5.0-1) which is a virtual package.
                           Depends: libmpcdec3 which is a virtual package.
                           Depends: libpulse0 which is a virtual package.
                           Depends: libsamplerate0 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
audacious [Not Installed]
audacious-plugins [Not Installed]
audacious-plugins-extra [Not Installed]
jackd [Not Installed]
libfluidsynth1 [Not Installed]
libjack0 [Not Installed]
libjack0.100.0-0 [Not Installed]
qjackctl [Not Installed]

Score is -9818

Accept this solution? [Y/n/q/?] 


---

### Post by saab on 2007-11-01
should I just do a new, fresh install?

---

