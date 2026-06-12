---
title: "Installed 7.10 and need to remove Dapper Drake"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by beno4433 on 2007-10-20
I recently performed a clean 7.10 installation in which my plan was to install it over my Dapper Drake version.  The installation was successful.  However, I must have performed the wrong partitioning steps because instead of installing Gutsy over Dapper Drake, I created two new partitions on my machine.  Now I have a multi boot system with XP Home, Dapper Drake, and Gutsy Gibbon on my machine. 

I'm very new to Ubuntu.  Plus the Dell Dimension, which is only used for testing purposes, has limited Ram and hard disk space.  Therefore I'd like to remove Dapper Drake and add the additional HD space to Gutsy Gibbon.

I tried to use gparted from Knoppix to free up the space, but for some reason, the program would not recognize all the partitions on my machine.

So here's my question to the community:

Is there a way in Ubuntu 7.10 to remove the Dapper Drake partition along with it's swap space and add the additional space to the newer version?  I assume I'll have to download some type of program to do this.  But I'm not sure where to look for it.

Any suggestions and comments would be greatly appreciated.

---

### Post by mikeyphi on 2007-10-20
Perhaps you might have better luck with Ubuntu gparted - download using Synaptic.
Just make sure you delete the correct partitions!!!!
So before you start check where your Dapper and Gutsy are: such as hda1 / sda2 or whatever!!

---

### Post by Paqman on 2007-10-20
You can also get [Gparted on it's own LiveCD](http://gparted.sourceforge.net/livecd.php).

---

### Post by beno4433 on 2007-10-20
I was able to get gparted to correclty show my Hard Drive Partitions.  However, given that I'm new to how linux shows partitions, I'm unable to determine which partition is Dapper Drake from Gutsy.  Here's what gparted shows.  

Primary Partition 02 - I know that's XP because it's NTFS  22.7 GB
Primary Partition 03 - /devhda3 (ext3)  8.14 GB

Under Primary Partiition 03 is an extended partition 04 /dev/hda4 with the following:

05 -  /dev/hda5 (ext3 with a status of Active) 5.39 GB
06- /dev/hda6 (linux swap) 305.89 MB
07 - /dev/hda7 (linux swap) 635 MB

Is there anyway for me to determine which version is installed on the partitions listed?  After that, I'm going to have to figure out the proper way to remove the Partition Dapper Drake and it's associated swap space and add it to Gutsy.

Thanks for you assistance

---

### Post by mikeyphi on 2007-10-20
"Is there anyway for me to determine which version is installed on the partitions listed?"

Look at you Grub page during the boot process - the list of options also states which partition each OS is on.

However I must say that your partition list looks strange: you might want to consider doing a fresh install by booting into the LiveCD ; running gparted and deleting all except your windows partition, then just install using the 'largest free space' option.

---

### Post by beno4433 on 2007-10-20
I agree that I should just do a reinstallation of 7.10.  My concern is my lack of experience with partitioning.  I'm going to give it a try, though.  I have nothing to loose on my Dell Dimension 4550.  Even though I want to try and keep the XP home installation, I must admit I never use it on this machine.  My primary machine is a Dell M70 laptop and  I want to eventually install 7.10 on it as well.  But I definitely want to keep XP Pro and use a dual boot installation.  I guess this is good practice.

---

### Post by cotcot on 2007-10-20
I also recommend using the GParted LiveCD to delete the dapper partitions and move the gutsy partitions.

---

### Post by beno4433 on 2007-10-20
Ok - I booted the 7.10 liveCD and opened GParted.  Just for a reference, I'll repeat what it shows.

/dev/sda1 - fat16
/dev/sda2 - ntfs

I know those are my XP home and dell utility partitions.  Here's the linux setup and the problems I see.

/dev/sda3 ext - I assume this is the primary partition because here's what's under it.

/dev/sda4 - extended
  /dev/sda5 - swap
  /dev/sda6 - ext3
  /dev/sda7 - swap

The problem is that /dev/sda4, /dev/sda5, and /dev/sda7 have a padlock next to them.  Does this mean I need to delete the /dev/sda3 and /de/sda6 partitions first.  And after that, I'll be able to delete the remaining partitions.

Please forgive me if all this is confusing.  I'm a newbie and therefore having difficulty expressing my situation.  Plus, I'm very apprehensive about making changes

---

