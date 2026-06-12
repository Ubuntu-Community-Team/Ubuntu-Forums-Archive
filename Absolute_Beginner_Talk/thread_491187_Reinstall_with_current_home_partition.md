---
title: "Reinstall with current home partition"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by BHelts on 2007-07-03
I'm having a problem related to [this thread]("http://ubuntuforums.org/showthread.php?t=490325").  Since I'm not going to figure it out on my own, i'm going to reinstall Ubuntu.
My question is this, Acting on advice from this forum, i've created a separate /home partition, when I reinstall Ubuntu with the existing /home partition, will my settings be in tact?  I know my data will be there, but what about settings?  programs?
thanks in advance for your help.

---

### Post by Ozeuss on 2007-07-03
reinstalling isn't that much of a hassle, but wouldn't you want to solve your problem? anyways, when you reinstall, you partition manually and specify the the /home partition. once you've installed, all your settings will be restored. so your settings will be intact, excluding maybe certain conf files of larger services, such as apache and samba. my advice anyway is to backup most of the various conf files (fstab, httpd, smb, sources.list, xorg, etc) to a folder in /home.

---

### Post by davidjmayo on 2007-07-03
> reinstalling isn't that much of a hassle, but wouldn't you want to solve your problem? anyways, when you reinstall, you partition manually and specify the the /home partition. once you've installed, all your settings will be restored. so your settings will be intact, excluding maybe certain conf files of larger services, such as apache and samba. my advice anyway is to backup most of the various conf files (fstab, httg isn't that much of a hassle, but wouldn't you want to solve your problem? anyways, when you reinstall, you partition manually and specify the the /home partition. once you've installed, all your settings will be restored. so your settings will be intact, excluding maybe certain conf files of larger services, such as apache and samba. my advice anyway is to backup most of the various conf files (fstab, httpd, smb, sources.list, xorg, etc) to a folder in /home.pd, smb, sources.list, xorg, etc) to a folder in /home.

Follow the backup advice to be safe

To confirm - All your /home settings will be intact as long as you don't format /home but you may need to check it is still set as /home during the install partitioning stage (it may default to unused space or something else). If you use guided partitioning just <go back> and check your partitions are correct, then continue the install

NOTE:  If you added anything from synaptic (or apt-get or aptitude) you will have to install these again then the settings will be intact but not until you restinstall them (for example I use thunderbird for email so I would have to install it again then all my emails, address book etc are just like they were before)

---

### Post by BHelts on 2007-07-04
thanks a lot, i appreciate it!

---

