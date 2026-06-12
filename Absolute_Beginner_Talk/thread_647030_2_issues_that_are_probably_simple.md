---
title: "2 issues that are probably simple"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by brandon333 on 2007-12-21
when you download something to install it opens in archive manager and then you click extract, and then..umm..then what, trying to download flash for youtube, its a tar file i open it and not sure which file to click on.


how can i get my computer to dual boot without doing the hold c or option thing.


ok 3 things why does my ubuntu drive say windows not linux when i have the option of booting

---

### Post by Gazneth on 2007-12-21
First thing downloading tarballs is a terrible thing for a user with little experience in linux. To install Flash player try opening a site with flash files, you tube works. Look at the yellow info bar at the top of your Firefox window, it will offer to install flash for you, if the auto mode doesn't work, try manual next just a check box in the window.  The safest way to install software is to use ADD/REMOVE programs  from the Applications window.  Or use Synaptic package manager in SYSTEM>ADMINISTRATION.

---

### Post by spiderbatdad on 2007-12-21
also flashplugin-nonfree is in synaptic. works well for me

---

### Post by Gazneth on 2007-12-21
I don't understand your boot question. About your drive question,  if you see a drive on your desktop labelled Windows, that is because it is your NTFS formatted Windows drive.  You can look at you ubuntu drive under PLACES>HOME>Filesystem. That will show your /  or root of you Ubuntu drive.

---

### Post by brandon333 on 2007-12-21
ok after installing gstreamer, flash and gnash from firefox pop up works fine however I noticed in all clips the controls are cut off.

---

### Post by brandon333 on 2007-12-21
> **Gazneth said:**
> I don't understand your boot question. About your drive question,  if you see a drive on your desktop labelled Windows, that is because it is your NTFS formatted Windows drive.  You can look at you ubuntu drive under PLACES>HOME>Filesystem. That will show your /  or root of you Ubuntu drive.

I would like to get to the screen where i have 2 hard drive picture 1 is my mac os other says windows but it is linux, getting to it is no problem as long as I hold down option my question is can i get to this without holding down option, 

the only thing showing up on my desktop is my external drive which is odd, not the linux partition or mac partition.


ok ok i went into that and clicked on mac drive and it then sent icon to desktop, 3 drives icons in file browser, my mac, external, and one called file system, you click on that then there is the home folder, then click into that and then me, shouldnt I be home, I am not root which could be the reson I am having issues not being able to do anything in the adept manager.

my ubuntu is formatted as dos.windows as far as osx is concerned i think this is wrong, or no?

---

### Post by Gazneth on 2007-12-21
Is your Firefox up to date?  I think a patch came out a few days ago.  If you haven't ran your autoupdate lately you can try that. It's the orange starburst that pops up in the system tray.  You could also try logging out then back in. That sometimes helps.

---

### Post by Gazneth on 2007-12-21
If you are on one of those shiny new Mac systems, I am Envious. :biggrin:  I don't know anything about their boot process though.  You may have to hold that option key though.  There Bios is totally alien to me.  If you want to see all your drives try PLACES>Computer

---

### Post by Gazneth on 2007-12-21
The one called File System is your Ubuntu drive at the root level it is labelled " / "  You can view it even if you aren't root. The folder you will mainly interact with is Home with your user name.  It holds all your user data, downloaded files , documents, photos and such.  You can format Ubuntu to almost any file system available in the installer and it will work fine, Ext3 seems to be the most popular. To update with Adept use your Admin password, it is the same as your regular password if you have admin priviliges. By default it is not necessary or recommended to have a ROOT password in Ubuntu.

---

### Post by brandon333 on 2007-12-21
> **Gazneth said:**
> If you are on one of those shiny new Mac systems, I am Envious. :biggrin:  I don't know anything about their boot process though.  You may have to hold that option key though.  There Bios is totally alien to me.  If you want to see all your drives try PLACES>Computer

Naw just a little new mac mini, lol, however I did have a 24 inch imac I took back due to screen issues (to glossy and the imacs are having major display problems,) and I am still stuck with a restock fee which has made me a no longer mac user, going to take back the mini I think it was 600 and doesnt even have a dvd drive, thinking of a dell maybe, I can get a much better pc for the money and without the osx what is the point of paying more for a mac, first day of linux and hooked!!

---

### Post by brandon333 on 2007-12-21
> **Gazneth said:**
> The one called File System is your Ubuntu drive at the root level it is labelled " / "  You can view it even if you aren't root. The folder you will mainly interact with is Home with your user name.  It holds all your user data, downloaded files , documents, photos and such.  You can format Ubuntu to almost any file system available in the installer and it will work fine, Ext3 seems to be the most popular. To update with Adept use your Admin password, it is the same as your regular password if you have admin priviliges. By default it is not necessary or recommended to have a ROOT password in Ubuntu.

I see the root in users and there is a password just dont know it, it's 2 characters shorter than mine, my directory is home/me, I just thought I would be /home ? my ubuntu is ext 3 according to gparted

---

