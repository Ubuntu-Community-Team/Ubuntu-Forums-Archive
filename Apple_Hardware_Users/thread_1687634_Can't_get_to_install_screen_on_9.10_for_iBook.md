---
title: "Can't get to install screen on 9.10 for iBook"
date: 2011-02-14
forum: Apple Hardware Users
---

### Post by CGUI on 2011-02-14
I am trying to install 9.10 on an older iBook that uses the Power PC installer. I have the image copied to a CD. I insert the CD and have the iBook boot from the CD. Yaboot loads and shows the partitions that can be booted. I've tried the live, live-nosplash-powerpc and live-powerpc. It then loads and shows the Ubuntu logo and loads files from the disk. However instead of getting the normal desktop to run the installer, it takes me to a Black looking desktop with a login screen where I can auto login or select other and enter a username and password. However, there was never a setup for the UID and PW when loading the disc. When I had version 5 installed, I ran the disc for 9 to upgrade and it did boot the correct login screen one time and took me to the desktop where the installer was. I went through the setup but kept getting errors about the partition trying to overwrite Breezy Badger. I then wiped the drive trying to install 9.10 fresh with no other version on it. However, this is the point I am stuck at now with the login screen. Does anyone know what the UID and PW should be or where to find it or maybe what is going wrong with the install? I did run the check through the partition in Yaboot and it verified that the disc was fine and the files were ok.

Thanks,
Sam

---

### Post by CGUI on 2011-02-14
Update: 

I am still new to the Linux environment, but for what its worth, I noticed this on startup as well.

Once I select the partition to boot in Yaboot, it goes to a black screen and starts loading items. It then pops up and says Shadow Passwords are now turned on then states the following (Not exact but close) 

'usr/ the rest of the path, then something along the line of user'ubuntu returned Error 1. Exiting. 

I am assuming its trying to create a login but for whatever reason is failing.

---

