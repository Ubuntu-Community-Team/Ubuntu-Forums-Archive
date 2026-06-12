---
title: "HOWTO: use a script to back up root (separate /home partiition)"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by bren on 2007-07-01
Hi All

EDIT: Some mistakes corrected
EDIT 2: It may be necessary to run the script a couple of times. 2nd time thro is much faster

Imagine

- you have spent some time installing Ubuntu and a few tweaks and a few software programs e.g. mp3 playback and getting your wireless laptop working
- you have a separate /home partition where all your data is

- you want to do a fresh install (its running slow or you messed with some settings etc) but you don't want spend all that time re-doing all the tweaks and installs

Solution
---------
[LIST=1]
[*]copy the two crucial config files to /home from your working system
[*]write a script to install the tweaks and software you have installed
[*]run ubunu LIVE CD and do a fresh install
[*]run your script which copies sources.list and xorg.conf back to the fresh install and then installs all your programs
[/LIST]

PROS[LIST=1]
[*]you can be up and running in a few minutes with a completely fresh system in a few minutes
[*]you don't have to re-google all those tweaks and hacks
[*]you don't have to take a "snapshot" backup of root - save disk space
[*]you only have to prepare the script once!
[/LIST]

CONS[LIST=1]
[*]you must prepare the script and be reasonably able with CLI to get the commands right (if you get into the habit of updating the script as you install new programs its very easy and quick)
[*]you must remember to take a copy of the 2 config files and put in your home directory before you do the fresh install
[/LIST]

Here is a copy of my script (for a Fujitsu Amilo A1650G laptop)
I called it restore.sh and saved it in ~/config along with my copies of sources.list and xorg.conf

If you want to use this method you should be able to hack my script to your needs quite easily
remember to make it executable.

When you have done it you can make executable and run it

```
chmod 744 restore.sh
./restore.sh
```

Comments welcome
:)

bren

```
# System Restore Script
# Purpose: To restore my most used applications and settings easily
# after a Ubuntu fresh install and to stop me forgetting all the software
# and tweaks I did after install.   Since I have a separate /home folder
# this script effectively means i don't have to back up root (/) and only have to
# back up my /home data
# Ubuntu 7.04 Feisty Fawn

# Step 1: Restore my sources.list file
# make backup
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
# copy in previously saved sources.list from my previously saved config directory
sudo cp /home/bren/config/sources.list /etc/apt/sources.list
# repair apt as it may be broken at time of first run thro
sudo apt-get -f update

# Step 2: Make sure I have all the security and software updates
sudo apt-get -y update
sudo apt-get -y dist-upgrade

# Step 3: Install some of my favorite programs
# sudo apt-get install frozen-bubble neverball chromium supertux kdf xmms xmms-skins totem-xine nvidia-glx xine-ui
sudo apt-get -y install ntfs-3g ntfs-config amarok k3b gparted kstars 
# add musicbrainz support for amarok - get tags for MP3s easily
sudo apt-get -y install libtunepimp5-mp3

# Step 4: Install programs that I have downloaded on my local hard disk
# Note: If I move these packages to a different location, I'll need to update this script
sudo dpkg -i /home/bren/download/deb/LimeWireLinux.deb

# Step 5: Restore screen resolution settings for my monitor
# Note: Do not do this unless restoring to a single pc
#sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
#sudo cp /home/bren/Config/xorg.conf /etc/X11/xorg.conf

# Step 6: Install the Adobe Flash plugin for Mozilla Firefox
# Note: This works with 32-bit Ubuntu only
sudo apt-get -y install flashplugin-nonfree

# Step 7: Sort out wireless
# Fujitsu Siemens AMILO A1650G
#
# get essentials so we can compile ACER_ACPI
sudo apt-get -y install build-essential
sudo apt-get -y install linux-headers-`uname -r`
#
cd /home/bren/download/acer_acpi-0.4/
sudo make install
sudo modprobe acer_acpi
sudo chmod 777 /proc/acpi/acer/wireless
sudo echo "enabled: 1">/proc/acpi/acer/wireless

# Step 8: Sort out keyring for wireless so i don't need to 
# keep typing the WPA pass phrase every time I connect to wireless
# this needs an edgy backport libary
# get this by temporarily switching to a different sources.list file because # I don't want this backport enabled normally
# copy temp sources.list which contains edgy backport to sources.listn
sudo cp /home/bren/config/edgybackport_sources.list /etc/apt/sources.list
sudo apt-get -y update
# add libpam-keyring
sudo apt-get -y install libpam-keyring
# copy sources.list back again
sudo cp /home/bren/config/sources.list /etc/apt/sources.list
sudo apt-get -y update
# Step 9: install gstreamer libraries and other codecs for mp3 and dvd use
sudo apt-get -y install gstreamer0.10-plugins-ugly
sudo apt-get -y install gstreamer0.10-ffmpeg
sudo apt-get -y install gstreamer0.10-plugins-bad-multiverse
sudo apt-get -y install gstreamer0.10-plugins-bad
sudo apt-get -y install ubuntu-restricted-extras
sudo apt-get -y install vorbis-tools lame sox ffmpeg mjpegtools
# install the key for medibuntu repositories
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
# refresh & get codecs
sudo apt-get -y install libdvdcss2 w32codecs 

# Step 10: Realplayer
# doesn't work!
sudo apt-get -y install realplayer realplay helix-player mozilla-helix-player

# Step 11: Gnome Xorg Display Manager
# GUI showing screens and resolution configuration
sudo apt-get -y install displayconfig-gtk

# Step 12: NTFS config
sudo ntfs-config

# Step 13: googleearth
# may cause crash and reboot
# uncomment and run again after step 14 has been successful
# sudo apt-get install googleearth

# Step 14: make sure that fglrx graphics driver is properly installed
# for my ATI X200M graphics card
# test afterwards by glxinfo | grep render
# and running test program glxgears (fps should be >500)
#
# more info http://groups.google.com/group/earth-linux/browse_thread/
# thread/6acf610c4de4ee01
# 
# and here
# https://help.ubuntu.com/community/BinaryDriverHowto/ATI
sudo apt-get -y install xorg-driver-fglrx
sudo apt-get -y install fglrx-control
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
# backup xorg.conf
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.restorescriptbackup
# copy in version of xorg.conf which has composite disabled 
sudo cp /home/bren/config/ /etc/X11/xorg.conf

# Finally: Reboot
sudo reboot  
```

---

### Post by paradoc on 2007-07-01
Thanks for this Bren!

It's a couple of months ahead of me yet but I can see that it's carefully done and thoroughly documented, and will serve as a comparison template for what I want to do as well.

Kind regards! LesN

---

### Post by elinav on 2007-10-04
Thanks - I have been looking for something like this for a long time. Too bad I found this AFTER I am re-installing my crashed HD...

Doron

---

### Post by bren on 2007-10-04
doron

i learned more since i made it...

please do not use my script as example of good one or of good practice...

see also forum sticky posts about install scripts being bad (automatix)

however, script does most of what it was intended to do :-)

bren

---

