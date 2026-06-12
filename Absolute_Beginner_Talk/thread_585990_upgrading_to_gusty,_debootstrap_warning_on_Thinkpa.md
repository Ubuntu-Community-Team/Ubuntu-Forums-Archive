---
title: "upgrading to gusty, debootstrap warning on Thinkpad T60, PLEASE HELP"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by mhedges48 on 2007-10-21
Today I had Feisty Fawn working beautifully on a Thinkpad T60p. In update manager, I chose to update to Gusty. Big mistake. During the downloads, several packages (locales, language packs, several others) failed to install. When the system restarted, my display was garbled and I could not get into the system.

I downloaded both the normal Gusty and the alternative Gusty to a CD (and verified ok) and both give me the same problems. 

I try to reinstall the system with the following partitions (just like how they were under Feisty, except I reformatted the root trying to do a clean install):
#1 primary 20GB K ntfs /media/sda1 (windows xp)
#3 primary 98.7MB K ext3 /boot
#7 logical 20GB K ext 3 /
#6 logical 51.9GB K ext3 /home
#5 logical 3.1GB F swap swap
#2 primary 4.9 GB K fat32 /media/sda2 (thinkpad recovery)

The only thing I formated from the Feisty days was the root (in order to try a clean install)

The installation arrives to about 68% of installing base system (console setup) and comes up with a red screen: 
!! Install the Base System
Debootstrap warning
Failure while configuring base packages.

I hit continue a few times and it installs APT and a few other things and then the red screen comes back and says: 
Unable to install initramfs-tools.

That's as far as I can get.

Any help is extremely appreciated as I have a presentation I have to do tomorrow and my files are on the /home partition and cannot be accessed from Windows (and I left my backup in another friggin country).

thanks very much
Matt

---

### Post by mhedges48 on 2007-10-21
fixed it by doing automatic partitions....

---

