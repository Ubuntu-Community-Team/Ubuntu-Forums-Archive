---
title: "How do I set up wireless internet?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by godfromdfo on 2008-01-26
Ok, I have been guided in the following thread: [http://ubuntuforums.org/showthread.php?t=678844](http://ubuntuforums.org/showthread.php?t=678844) how I can set up my buffalo driver for wireless like this guy: [http://ubuntuforums.org/showthread.php?p=4159357](http://ubuntuforums.org/showthread.php?p=4159357) HOWEVER! I have never manualy set up a wireless internet connection before on a windows pc let alone linux :( so, umm can somone explain what I do please? (I will install ubuntu once I know what to do....) for example on windows I just installed Client Manager 3 and clicked on AOSS and this machine connected with the one down stairs... but, i'm assuming client manager 3 won't work with linux and thus I would have to manualy set up my wireless internet... can somone please explain how? :lolflag: <-- goku =\\

\m/  :guitar: \m/ 

thanks,

Cloud

PS: The pc with the router is running xp

---

### Post by mrphud on 2008-01-26
Setting up wireless is just a router thing. I have a dual boot and I set up my linksys router in windows and it works great when I boot up ubuntu. Try accessing your router and setting it up manually. There are some good help pages on Wikipedia depending on what type of router you have.

---

### Post by ugm6hr on 2008-01-26
The OP is a bit confusing...  So let me start by summarising what I understood:

1. You have a wireless router (Buffalo brand)
2. A Windows XP computer is connected to the router by ethernet (cable).
3. The computer (upstairs) has a Buffalo wireless card (? WLI-U2-KG125S), and currently connects to the router wirelessly (and has XP on it at the moment).
4. You want to install Ubuntu on the computer upstairs, and maintain your wifi internet connection.

If that is all true, according to the post you have referenced ([http://ubuntuforums.org/showthread.php?p=4159357](http://ubuntuforums.org/showthread.php?p=4159357)), you will need to install ndiswrapper on your Gutsy installation.

So, make sure you have the following files available (e.g. on a CD or USB flash disk) when you install:
netg125s.inf usb8023.sys rndismp.sys (all from the Buffalo driver CD somewhere, apparently)

Also these (assuming you are going to install the "regular computer" 32 bit Ubuntu):
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb)

Then install Ubuntu as normal.  After booting up into your newly installed Ubuntu, follow the rest of this...

Put all of the above files / packages in your "home" directory (i.e. /home/username), then enter (copy and paste) the following commands in Terminal:
```
sudo dpkg -i ndiswrapper-common_1.43-1ubuntu2_all.deb
sudo dpkg -i ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb
sudo dpkg -i ndisgtk_0.7.2-1ubuntu1_i386.deb
```
These install ndiswrapper (and also the ndisgtk GUI, in case you want to try it - but it is a bit buggy)

Then these commands (taken from [http://ubuntuforums.org/showpost.php?p=4159357&postcount=2):](http://ubuntuforums.org/showpost.php?p=4159357&postcount=2):)
```

sudo ndiswrapper -i netg125s.inf
sudo cp usb8023.sys rndismp.sys /etc/ndiswrapper/netg125s/
ndiswrapper -l
```
This should comfirm that the adapter is present.  The first 2 select the correct driver to be used.

Then continue (if the adapter is confirmed):
```
sudo depmod -a
sudo modprobe ndiswrapper
iwconfig
```
This should show the wifi device as wlan0.  These commands tell ndiswrapper module to run.

Then continue (if wlan0 OK) - from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de)
```
sudo ndiswrapper -m
gksudo gedit /etc/modules
```
Add *ndiswrapper* to the bottom of this file (text file should be opened), and save it.
These commands tell ndiswrapper to work every time you login (so you don't have to repeat the process).

I know this sounds a bit convoluted, but it is probably safer to use text commands than the GUI.  Nevertheless, you *could* try the GUI if you wanted...

---

