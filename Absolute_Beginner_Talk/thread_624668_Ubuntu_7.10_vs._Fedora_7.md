---
title: "Ubuntu 7.10 vs. Fedora 7"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by anilbhx on 2007-11-27
My  experience with Ubuntu . I have been using Fedora for sometime now . I decided to try out Ubuntu mainly because the visuals looked so attractive.

Some of things I value apart from ease of Java, Flash plug-ins  installation   etc was that it located the fedora and XP installations and put them in the Grub menu.lst file.

The programs that don't start for my setup are these :

Earth3d , Blender 
till now . 
I missed the boot loader equivalent where one does not have to edit the menu.lst grub file directly.

Ubuntu is now my preferred OS , and would be grateful for any advice regarding the above programs.

Another strange experience : 
I installed a HP 1315 printer and scanner without any problems with the standard 7.10 setup . However after maybe some changes which I cannot recollect. It stopped working and no amount of installation and re-installation could I get it back . I suggest somewhere in the support files it should be mentioned which packages are required for printing scanning . I installed the latest HPLIP package from sourceforge and now the printer is back .

---

### Post by taurus on 2007-11-27
What graphic card do you have and have you installed a driver for it if you plan to do some 3D stuff?

---

### Post by anaconda on 2007-11-27
how did you install them?
I installed blender and earth3d from the repositories with apt-get and both of them work very well.

(Just asking, because suprisingly many people are installing programs from .rpm:s)

---

### Post by anilbhx on 2007-11-27
The graphics card is a pro-savage built-in to the mother board. I cant remember the other details . There is another 3d program ( without animation ) which is working. Wings I think .
I installed everything using Synaptics  Manager . 

-------
Finally this is working on Fedora 7 which I assume should be similar as far as the drivers are concerned...

---

### Post by gn2 on 2007-11-27
GrubEd is a GUI Grub editor, but there are problems with 7.10.

It's being worked on though: [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

---

### Post by houstonbofh on 2007-11-27
> **anilbhx said:**
> I installed the latest HPLIP package from sourceforge and now the printer is back .
This is a type of thinking you need to hold back on.  Adding custom packages and compiled drivers often breaks thing if you do not know a lot about Debian.  Hacking Debian is different from hacking Fedora, and it will take some time to learn.  For you, I would start with a clean install, and add in the commercial, winhq an medibuntu repos.  If those don't have the stuff you need, try getdeb, but keep it clean.  That may solve a lot of your problems...

---

### Post by anilbhx on 2007-11-28
> **houstonbofh said:**
> This is a type of thinking you need to hold back on.  Adding custom packages and compiled drivers often breaks thing if you do not know a lot about Debian.  Hacking Debian is different from hacking Fedora, and it will take some time to learn.  For you, I would start with a clean install, and add in the commercial, winhq an medibuntu repos.  If those don't have the stuff you need, try getdeb, but keep it clean.  That may solve a lot of your problems...

I almost did a clean install. I can still do that ... Perhaps will. WIll have to look up how to add repos to synaptics. Did not see anything anywhere..

---

### Post by houstonbofh on 2007-11-28
This is a script I run on new Gutsy systems...  You can use "Software Sources" in Synaptic, or directly from System --> Administration, but this could teach you a bit as well.  Good luck.
> #!/bin/sh
# Ubuntu Update Script (Gutsy)
#
# This is a script to update a default install to 
# a fully functional system. Most things are automated,
# but a few things still need to be done by hand.
#
# NTP Config
# Set the clock to update automatically from
# us.pool.ntp.org
#
# Note: Sudo must be enabled for this to work.
# (Type 'sudo ls' and the passowrd before running
# this script)
#

# Add extra repositories

# Medibuntu
wget -q [http://medibuntu.org/repo/medibuntu-key.gpg](http://medibuntu.org/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo wget [http://medibuntu.org/sources.list.d/gutsy.list](http://medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

# Wine HQ
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

# Refresh repositories
sudo apt-get update

# Install everything

sudo apt-get install ssh traceroute p7zip unace rar xfonts-intl-european faad ffmpeg ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse lame liba52-0.7.4 libartsc0 libdc1394-13 libdvdread3 libfaac0 libfaad2-0 libgsm1 libid3tag0 libimlib2 liblame0 libmad0 libmjpegtools0c2a libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 libquicktime1 libsidplay1 libswfdec0.3 libxine1-ffmpeg libxvidcore4 libxvmc1 mjpegtools ntp sox vorbis-tools libdvdcss2 w32codecs ogle-mmx ogle-gui streamtuner streamripper


---

