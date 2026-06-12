---
title: "DVD help"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Hayter on 2006-01-26
I know this is going to sound stupid, but when reading up before installing ubuntu, I read something about needing to run a code to get DVDs to play. But I can not remember where that was. Can anyone help?

Also is there a list of command line somewhere that I can look at?

---

### Post by mips on 2006-01-26
Thinking of libdvdcss2 ?

---

### Post by mips on 2006-01-26
Look at [http://ubuntuforums.org/showthread.php?t=87481](http://ubuntuforums.org/showthread.php?t=87481)

All those howto's are located here: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by Hayter on 2006-01-26
I have tried the following command line:

sudo apt-get install libdvdcss2

and it says:

Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libdvdcss2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 99.6kB of archives.
After unpacking 270kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libdvdcss2
Install these packages without verification [y/N]? y
Get:1 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free libdvdcss2 1.2.9-1plf3 [99.6kB]Fetched 99.6kB in 0s (191kB/s)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package libdvdcss2.
(Reading database ... 72322 files and directories currently installed.)
Unpacking libdvdcss2 (from .../libdvdcss2_1.2.9-1plf3_i386.deb) ...
Setting up libdvdcss2 (1.2.9-1plf3) ...

W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


I am a newbie, and I have no idea what this means? Can anyone help me? All I want is DVD playback.

---

### Post by plexi50 on 2006-01-26
Try using Automatix, very easy way to get all the needed files for a new install. Watch the terminal screen while they run to see what would happen if you did it manually. The error you recieved was due to repository being used.

---

### Post by Perfect Storm on 2006-01-26
Did you run **sudo apt-get update** to see if it solved your problems?

---

### Post by Hayter on 2006-01-26
Thanks guys, now using automatrix hopefully it will work.

---

