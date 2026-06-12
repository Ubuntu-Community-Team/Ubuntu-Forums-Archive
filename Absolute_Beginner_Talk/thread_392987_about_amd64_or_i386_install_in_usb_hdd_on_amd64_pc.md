---
title: "about amd64 or i386 install in usb hdd on amd64 pc"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by svvsrgrs on 2007-03-25
I have amd 3800+ a8n-e x300se and fujitsu40gb usb hdd.
the system runs ubuntu 6.10 64-bit 
Boots (grub)temporarly from 6.10 i386 live cd trough the option boot from 
first hdd,in a previous instalation ihad selected grub to be installed
in (fd0) and it could  boot with no i386 cds help [i never managed to 
boot grub from the usb hdd],if i have the 64bit cd(not the live) and select boot from
first hdd nothing happens.otherwise all other is ok.
   Another i like to mention is an attempt i did to install in this system
the i386 6.10 i only managad it by deleting all partitions with another
os systems cd this os tthat has much much viruses after making the instalation
of the 64bit 6.10 until the point that says configuring systems clock in which
i pressed back and then quit instalation ,open then with i386 6.10 live cd and
instaling.an attempt to install i386 from the begining didnt work only this i just mentioned. 
      I have managed the 64 bit 6,10 to run the restricted media files
but for a newbe thinks are not easy
sudo apt-get install ia32-libs
sudo apt-get install lib32asound2
sudo apt-get install lib32ncurses5 
sudo apt-get install ia32-libs-sdl
sudo apt-get install ia32-libs-gtk 
sudo apt-get install lib32stdc++6 
sudo apt-get install  ia32-libs-openoffice.org2(this didnt worked in my sys|)
sudo mkdir /usr/lib/win32
Fetch the Win32 codecs from [http://www.people.virginia.edu/~drf8f/MPlayer/releases/codecs/essential-20060501.tar.bz2](http://www.people.virginia.edu/~drf8f/MPlayer/releases/codecs/essential-20060501.tar.bz2)
Unpack it and install to /usr/lib/win32.i did installed by writin in terminal sudo nautilus
then put the iside of folder there not the  folder (copy paste)
then download vlc player from the menu add remove aplications

---

