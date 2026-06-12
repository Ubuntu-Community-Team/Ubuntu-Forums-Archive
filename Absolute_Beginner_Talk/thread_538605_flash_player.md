---
title: "flash player?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Staff on 2007-08-30
im using edgy and when i go on a lot of websites, it says that not all content could be displayed - click here to install plugins. when i do that, it shows adobe flash player needs to be installed. if i try to install, it fails. i think this is because it's a windows file. is there a way to install it on ubuntu? or should i install an alternative flash player? how do i do it.

thanks :D

---

### Post by Kobalt on 2007-08-30
To install the flashplayer, open up the Terminal and run this command line : ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```
Then restart your Firefox, and you should be done.

---

### Post by shearn89 on 2007-08-30
Its not natively supported in some cases, as it's proprietary software. Check [here]("https://help.ubuntu.com/community/RestrictedFormats/Flash") for more info, and some free alternatives...

---

### Post by Staff on 2007-09-01
real problem! 


< NAME >@< NAME >-desktop:~$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11
Suggested packages:
  msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree gsfonts-x11
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 26.5kB of archives.
After unpacking 287kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main gsfonts-x11 0.20build1 [10.6kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse flashplugin-nonfree 7.0.68~ubuntu3 [15.9kB]
Fetched 26.5kB in 0s (37.5kB/s)        
in
errPreconfiguring packages ...
m
mins
Selecting previously deselected package gsfonts-x11.
(Reading database ... 93114 files and directories currently installed.)
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20build1_all.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_7.0.68~ubuntu3_i386.deb) ...
Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading...  done.
automatic installation failed due to network problems or upstream changes




automatic installation failed!? ='[
what now?
 
thank you

---

