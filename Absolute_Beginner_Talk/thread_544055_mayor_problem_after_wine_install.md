---
title: "mayor problem after wine install"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Escipion on 2007-09-05
Hello I really need help with this, I just installed WINE following this guide: [https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64)

All was ok but when I (stupidly) ran this part: Sidenet Script

[B]If you followed the instructions above you may install the Sidenet script by hand. Sidenet adds fonts, a virtual c drive in you home folder, and sets up the windows dll's in the wine registry, however this method is not supported or recommended by the Wine developers. Users who installed with the below install script do not need to run the Sidenet setup because its included. Please do not run this setup script with sudo.

[WWW] Download the file to your desktop. Open a terminal and enter

cd ~/Desktop 
tar -xzvf sidenet.tar.gz sidenet

Then we change the directory and run the script.

cd ~/Desktop/sidenet 
./setup[/B]

It changed all the links in my computer directory to "filesystem.desktop" "HP_RECOVERY.drive", I can get to them in my places but the real problem is when I go to network and get a file called: "smblink-root" and can't access the files on other wintoys based computers. It used to say "microsoft windows network"

It seems it turned all my folders in network and my computer to files.

I already uninstaled wine and I guess I did the same for the sidenet because when I typed "sudo apt-get uninstall wine --purge" it asked me to uninstall the not nesesary  sidenet leftovers

I'm running Feisty 64 on a turion 64 x2 laptop HP model TX1030la and compiz-fusion.

I've tried looking everywhere help will be very welcome.

Thanks in advance to all the ubuntuforums.org community.

---

### Post by bone2006 on 2007-09-07
I'm running wine, but it was as simply as following this [http://tinyurl.com/ngonb](http://tinyurl.com/ngonb)
Just add it to the repository and grab it.  I never had a problem with wine in the 64 bit version of ubuntu

---

