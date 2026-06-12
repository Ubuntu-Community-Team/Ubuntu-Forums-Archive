---
title: "Setting up dual boot.. unusable screen config"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by pumpa on 2007-08-12
Hey, im pretty new to ubuntu but ive set up one dual boot system before and at the moment im currently trying to get a dual boot running on my laptop wich is running a core 2 duo t5500 1gb ram and a X1700 card. 

I have Xp installed and everything running fine on that front except when i insert the fiesty disc and try to install it works through a few things and then i get the following error..

X Windows System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
CUrrent Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
Before reporting problems check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version
Module loader present
markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/xorg.0.log", Time sun etc etc 
(==) using config file: "/etc/x11/xorg.conf"
(EE) VESA(0): No matching modes
(EE) screens found, but none have a usable configuration.

Fatal Server error:
no screens found

then it disables x server after i press ok and then restarts GDM giving me a command line to type into.

ive looked around the net for a few hours but havent found much help.

---

### Post by steve.horsley on 2007-08-12
I take it this is the live CD that's not starting properly? IOf so, I woudl suggest you use the "alternate" installer CD which is text based, and then sort out the X configuration on the installed system (if it turns out that you need to).

---

### Post by JTux on 2007-08-12
1. If you downloaded one of the .iso files and burned the disc, Did you check the md5 sum of the .iso file?
If you haven't follow this howto,
[HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

To get the hashes go here,
[UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

You will have to download again if it fails the test
For more info have a look in this thread
[http://ubuntuforums.org/showthread.php?t=516889&highlight=md5sum+check]("http://ubuntuforums.org/showthread.php?t=516889&highlight=md5sum+check")

2. If this isn't the problem post the resolutions supported by windows along with the output from the following code ```
cat /etc/X11/xorg.conf
```

you should enter this in a terminal ( Applications->Accessories->Teriminal )

Hope this helps:)

---

### Post by pumpa on 2007-08-14
Ok, well i just finished my install after downloading the alternate CD installer. It installed fine partitiond all the drives ok then i selected ubuntu from the boot menu and then loads up a black screen with a bit of writing telling me to type my username 
then that screen flashes, then returns to it, flashes again then i get the same "failed to start the X server (your graphical interface) it is likely that it is not set up correctly. would you like to view the X server output to diagnose the problem?"

pressing yes then opens up the same error message as i posteed in my first post. any ideas?

---

### Post by pumpa on 2007-08-14
sorry forgot to post this in last post...
it returns me then to the black screen to log in and after i log in i typed 
cat /etc/X11/xorg.conf

i then received the following on screen:

SubSection "Display"
Depth  16
Modes "1024x768" "800x600" "640x480"
End SubSection

SubSection "Display"
Depth  24
Modes "1024x768" "800x600" "640x480"
End SubSection
 End Section

Section "serverLayout"
identifier "default layour"
screen "default screen"
input device "generic keyboard"
input device "configured mouse"
input device "stylus"   "sendCoreEvents"
input device "cursor"   "sendCoreEvents"
input device "eraser"   "sendCoreEvents"
inputdevice "synaptics Touchpad"
End Section

Section "DRI"
Mode 0666
End Section

---

### Post by pumpa on 2007-08-14
bump.

any ideas would be great. im confused as hell

---

### Post by SpeedRazor on 2007-08-15
I had this same problem with an Asus F3JP with x1700 mobility.

The only way I got it to install was to first install Ubuntu 6.06 LTS, upgrade to 6.10 using the instructions here:

[http://www.ubuntu.com/GetUbuntu/releasenotes/610](http://www.ubuntu.com/GetUbuntu/releasenotes/610)

And then finally upgrading to 7.04 using the instructions here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

It's a little bit more work but it got it working for me without the unusable screens error.

---

