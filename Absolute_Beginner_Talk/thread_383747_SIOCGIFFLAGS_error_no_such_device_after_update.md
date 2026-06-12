---
title: "SIOCGIFFLAGS error: no such device after update"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by huntnplay on 2007-03-13
ok, i got this SIOCGIFFLAGS error in ubuntu, and it idnd't allow me to connec to my internet i have a wireless connection inside my house. so i reinstalled the system, erasing everything on the hdd. now, it installed perfectly, and it was up and running, then it gave me an option to install updates, it had 139 updates as of 03/13/07, so i installed all of them thinking they are all beneficial and requiired. well, after the update, i restarted and am bakc to square 1, i get the same error again, the eth1 was working after the format, and new install. but after updates it has been giving me this error, siocgifflags error, no such device. i cannot connec to the internet someone help me out. thanks

---

### Post by SactoBob on 2007-03-14
It is very unlikely that installing the updates broke your wireless connection.
What did you do to get your wireless working?
Did it work out of the box, or did you use a native driver plus firmware, or ndiswrapper?

For example, if you used ndiswrapper successfully, but forgot to use
sudo ndiswrapper -m

Then ndiswrapper will not load at boot, so every time you boot, you would have to
sudo modprobe ndiswrapper.

Also, what kind of card and chip are  you using, that would be helpful.

But if your card worked initially, that is good news, it should be fine.

What does iwconfig report?

---

### Post by boozker on 2007-03-16
The exact same thing happened to me except i have Internet, but it says that i don't have a connection. Hope this gets resolved. Yes, this after the update also.

---

### Post by huntnplay on 2007-03-18
i got that error after the update, and i read somewhere else on the forums that this problem arises due to the updated kernel. now, i installed it all over again, and the wireless internet is working, and it is showing me that I have 140 updates, but I am not installing any of those updates, dont know which one is kernel related, or which update is causing this problem. so far, i can use the internet great, hopefully someone can show light to which update file causes this problem.

---

### Post by goodgord on 2007-03-19
Hey folks,

I'm a linux n00b, but I managed to fix the problem by following the instructions from koshari over in [this thread]("http://www.ubuntuforums.org/showthread.php?t=288649")

Installing the updates absolutely did break my wireless connection on my HP Compaq nx9010.

It looks like the new kernel update somehow re-introduces a bug that was originally reported [here.]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/64661")

Anyway, assuming you have a prism wavelan 2.5 chipset (check device manager), you can fix the wireless network and safely install all 140 updates : ^)

---

### Post by mychaelus on 2007-08-27
I had the same problem after an update. Reinstalling ndiswrapper fixed it. 

During the reinstall, I noticed that ndiswrapper utils had been removed or disabled by the update and that the bcmxx driver had to be blacklisted again. 

The instructions for installing ndiswrapper I used, which are the clearest I've found, are located here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) . If you already have the .deb packages in your home folder, and if the appropriate WIndows driver (both .inf and .sys files) has been placed in a directory in your home folder,  you can follow the instructions starting at section 3.1.  It will only take a couple of minutes.

To be clear, I have the following .deb packages in my home folder
ndiswrapper-common_1.38-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
ndisgtk_0.6-0ubuntu3_all.deb
I have the .inf and .sys files for my windows driver in a home folder called "drivers"
For my card, those files are "bcmwl5.inf" and "bcmwl5.sys"

Then I can just run this block of commands to set up ndiswrapper to activate my card:
sudo modprobe -r ndiswrapper 
sudo apt-get --purge remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo ndiswrapper -i ~/drivers/bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

Added later: to make sure ndiswrapper is launched at startup, open /etc/modules (sudo gedit /etc/modules) and add the word ndiswrapper to the bottom of the list, then save and close.

---

### Post by mychaelus on 2007-08-27
I also recommend using Wicd instead of Ubuntu's Network Manager.  ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/))  With Wicd, I know immediately if my ndiswrapper installation has been successful, because Wicd connects right away and a green bar appears in the top panel of Ubuntu. (Wicd has to be installed and configured already, of course, but it's very easy.)

---

