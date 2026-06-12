---
title: "Cannot modprob rt61"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by dellis on 2007-10-27
I've been trying to install RT61 drivers for Linux but have failed here...

I've gotten to the step when I should "sudo modprobe rt61" and I get an error:

Fatal: Error inserting rt61 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/rt61.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Dmesg says: 

rt61: Unknown symbol pci_module_init

I'm sorry, I'm new to Ubuntu.  I've looked for some solutions but haven't found any explained well enough for me.  I would appreciate any help.

---

### Post by dellis on 2007-10-27
bump

---

### Post by kevdog on 2007-10-27
Did you compile the rt61 drivers from the serialmonkey website, or did you get them from the ra website?  Just trying to figure out where you got your original rt61 driver -- is this the built-in driver?

---

### Post by dellis on 2007-10-27
I got the driver from the ra website.  I can get serialmonkey - should I do that?  How do I uninstall my existing driver?  thanks!

---

### Post by dhopley on 2007-11-17
Dear Dellis , 
Hi , I am using a Silan Electronics Ethernet card SC92031 (which I think is a similar card to the rt61) for which I had supplied a sc92031-2.6.4.tar.gz CD . In Ubuntu 7.04 after opening the cd to the archive manager I did the following on the terminal command line screen :
cd /home/derek/sc92031-2.6.4/src
sudo aptitude install
sudo aptitude install build-essential
sudo make
sudo make install
sudo cp sc92031.ko /lib/modules/2.6.20-16-generic/kernel/drivers/net
sudo depmod -a
sudo modprobe sc92031
and this gave me an internet connection on eth0 . 
On repeating the exercise after the upgrade to Ubuntu 7.10 with /lib/modules/2.6.22-14-generic/kernel/drivers/net 
it fails on modprobe with Dmesg pci_module_init unknown symbol and this looks like a similar problem to yours , did you have any success later ? Meanwhile of course I've reverted to using modules 2.6.20-16 , so far with no difficulty ,  
Derek

---

### Post by dhopley on 2007-11-18
Dear Dellis , 
Hi , I don't know if this might be of any good to you but I'm running Ubuntu 7.10 dual booting with Windows 98SE , which of course had it's own ethernet card driver set up on the originally supplied CD . Using the package ndiswrapper (which seems mainly for wireless connections but works fine with my ethernet card) , my network connection is OK , basically invoking the Windows driver mechanism . Set up as follows :
To check ndiswrapper is installed :
sudo ndiswrapper 
then do it , in my case the source driver file (inf) is a FAT32 file on my Windows drive mounted as /media/HDA1/EthCard/Win98se :
sudo ndiswrapper /media/hda1/EthCard/win98SE/netslnt.inf 
To check if it's worked :
sudo ndiswrapper -l     
Next prepare to load with : 
sudo depmod -a
and :
sudo modprobe ndiswrapper
In my case the network connection icon revolved and was replaced by a TV type icon and the internet connection was up and running ! :
Finally to invoke regularly on booting up :
gksudo gedit /etc/modules 
and add a line : 
ndiswrapper
Hope it may be of some help ,                                              
Derek

---

