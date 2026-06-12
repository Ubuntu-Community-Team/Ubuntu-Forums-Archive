---
title: "VM ware"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Rootwad on 2007-08-08
Does anyone know if iVM Ware will work in 7.04. thanks

---

### Post by Rocket2DMn on 2007-08-08
Yes, it does
[https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware) (Ubuntu in a VM)
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) (VM in Ubuntu)
^ for your reference.  Enjoy!

---

### Post by doogy2004 on 2007-08-08
I have it installed by:
sudo apt-get install vmware-server

but I have not had any luck getting it to work, yet.

---

### Post by zvacet on 2007-08-08
Go to the synaptic and install packages related to vmware server(modules...).

---

### Post by Rocket2DMn on 2007-08-08
Here are some options to help out:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) (older thread)
[http://ubuntuforums.org/showthread.php?t=342631](http://ubuntuforums.org/showthread.php?t=342631) (newer)
I have no setup a VM before, but there are a lot of threads out there to help you get started and troubleshoot, so have a look around.  Good luck.

---

### Post by Gary.M on 2007-08-08
I recommend you deinstall it the same way you installed it.

Then go to Vmware's site and find the download for Vmware player V2. Save it somewhere (your desktop?) Its the tar installer you want. Also search the Vmware site for their user manuals. There is one for the Vmware Player V2. Download that. Read the manual and follow the install instructions. When installing just hit enter on all the questions to accept the defaults. Hopefully it will all go without a hitch.

Next go to [www.easyvmx.com](www.easyvmx.com) and use the V2 machine creator. Download the machine you create and install the OS you want in the new machine.

There is alot on these forums about using vmware. I followed some of the forums advice first and then later moved from that to what I have outlined here. It is straightforward and very easy.

Vmware have user forums for the Player and the support there is pretty good.

The player is rock solid.

---

### Post by anewguy on 2007-08-09
If you install VMWare-Server from the repositories, you should be okay.  I've done that and had others do it with no problems.  VMWare-Server is super easy to use.  One thing you must do before you actually try to run it (could be your current problem) is you must add yourself to the vmware group.  Go to system/administration/users and groups, then click on manage groups, scroll through the list until you find vmware, then check your userid so it is included in the group.

The instructions I found for VMWare-Server on Feisty also gave the contents of a file you must copy/paste in place of the current contents of the file.  Please see:

[https://help.ubuntu.com/community/VMware/Server#head-4e9a466bc9b9bb8a16513719d0dd72fe126bb2f5]("https://help.ubuntu.com/community/VMware/Server#head-4e9a466bc9b9bb8a16513719d0dd72fe126bb2f5")

:)

---

### Post by Gary.M on 2007-08-09
But if you install into a new machine on Vmware Player V2 you get USB 2.0 support... that isn't there in server... server also eats more of your machines capability...

---

### Post by anewguy on 2007-08-09
Well, I haven't dug that deep into USB support, but I have used the USB that is in server with no problems.  I also haven't noticed a VM in VMWare-Server running slower than VMWare-Player.  Given the much greater flexibility with Server (things like creating and changing your VM without needing to know what to put in the .vmx file, etc.) have sold me on server.  I don't have to worry about finding a pre-created VM as I just create my own the way I want it.  Maybe I'm just lucky, maybe I don't run the same sorts of things in my VM's.:)  I also don't have an external USB file system, so I don't have experience in that if that is what you are looking for.  I believe there is something you have to do in /etc/fstab to mount a USB file system.

If performance seems down and if USB doesn't work satisfactory please post back here looking for help to specifically change those 2 aspects.:)

Good luck!  :):)  I really love using VM's!

---

### Post by anewguy on 2007-08-10
BTW - the USB question isn't included in Rootwad's original post - he wants to know if VMWare runs in 7.04.  The answer is yes.  I provided the link I did and suggested going through the synaptic package manager because then you don' have worry about dependencies, etc., nor the  patch for server to work in 7.04.  I followed the site exactly - downloading via synaptic, then making the contents of the file match those shown on the site, and bingo everything was running.  I personally would never give up the flexibility the VMWare-Server offers to go to just VMWare-Player - it's a step down, not up.   I have downloaded other LiveCD's and install cd sets for other LInux's and using server I have them up and running by just pointing the vm cd drive to the iso of the LiveCD or install disk, all through the gui.  I've also had Windows 98, Windows XP, etc., on and off in VM with so easy setup it's almost ridiculous.  I've had VMWare Player before, and got rid of it to upgrade to VMWare Server.  It only makes sense.:)   (you'll find that same suggestion in innumerable posts about virtual machines on this forum).

---

### Post by cwmoser on 2007-08-10
Anytime I install anything with Ubuntu, I document what I did and save it in my notes folder.

For VMware, I had some trouble the first time and it was solved via the folks here.  Since that time I have used the following notes I got from this forum that has made it easy for me to reinstall VMware.  The following might help:


Vmware Notes:


Remove Vmware:

	sudo rm  -r  /etc/vmware

	apt-get  remove  --purge  vmware-server




INSTALLATION:

Install via:  How To Install Vmware On Ubuntu 7.04 (Feisty Fawn)

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

his tutorial provides step-by-step instructions about how to install the free VMware Server on an Ubuntu 7.04 (Feisty Fawn) system. With VMware Server you can create and run guest operating systems ("virtual machines") such as Linux, Windows, FreeBSD, etc. under a host operating system. This has the benefit that you can run multiple operating systems on the same hardware which saves a lot of money, and you can move virtual machines from one VMware Server to the next one (or to a system that has the VMware Player which is also free). 
Build Environment
Make sure you have the needed build environment and tools to compile the vmware modules for the kernel.
aptitude install linux-headers-`uname -r` build-essential
aptitude install xinetd
Downloading VMware Server
Vmware Server can be downloaded from:
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) 

After accepting the EULA grab the vmware server .tgz file (around 102MB).
Note: As of right now VMware Server won't compile correctly on Feisty without patching the vmmon file.
Patch information can be found here: [http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)
The patch can be downloaded here: [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)
Installing VMware Server
Untar the VMware Server package:
tar -xzf /Path/To/VMware-server-1.0.3-xxx.tar.gz
Change into the install directory:
cd vmware-server-distrib
Run the installer:
sudo vmware-install.pl
Choose defaults to questions until it asks:
Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes]
Enter no and quit the install. To install the patch cd back to your start directory:
cd ..
Untar the patch:
tar xvzf /Path/To/vmware-any-any-update109.tar.gz 
Enter the directory: 
cd vmware-any-any-update109
Run the patch script:
sudo ./runme.pl
It should prompt you to run vmware-config.pl, choose yes at this time. If it doesn't you can always run the config script manually:
sudo vmware-config.pl
Again you can hit enter to choose the defaults to all the questions, though you will probably want to manually choose which networking features you want. To access the server run
vmware
for the VMware Server Console.

---

### Post by anewguy on 2007-08-10
Yes, if you already have server or player installed you need to do what you said to delete them (there is actually more to it to completely remove either on), but it didn't sound like IRootwad had it installed yet - if he did he didn't say so.  As far as installing, I'm telling you it's much easier it you follow the link I posted, you'll get it via synaptics, with all the dependencies  etc., handled for you, and you DO NOT NEED THE PATCH if you do what it says on the page I pointed to.:)  Also, if installed correctly, you should be able to access VMWare Server from the Applications/System Tools menu.

---

### Post by Gary.M on 2007-08-10
Well my experience with Player V2 from the Vmware site, and following their user manual install procedure, was equally uneventful. It just installed and worked. In my case I wanted a reliable XP VM to run a specific app in, and having USB support for my non-linux supported Canon scanner was a bonus. USB 2.0 is needed for that... just trying to lay out the options clearly. Not everyone wants to install, trial, and play with multiple OSs... Some of us just want to work...

---

### Post by sparau on 2007-08-10
fyi - server running on 64 bit 7.04 here - although i probably stupidly built it rather than got it from synaptic...

and to cwmoser - damn you're a clever one - writing things down !!!

bugger - and i have to relearn everything everytime i do it :) :) :)

---

### Post by anewguy on 2007-08-11
> **Gary.M said:**
> Well my experience with Player V2 from the Vmware site, and following their user manual install procedure, was equally uneventful. It just installed and worked. In my case I wanted a reliable XP VM to run a specific app in, and having USB support for my non-linux supported Canon scanner was a bonus. USB 2.0 is needed for that... just trying to lay out the options clearly. Not everyone wants to install, trial, and play with multiple OSs... Some of us just want to work...

Hey Gary,  did the scanner just not work at all in VMWare Server?  It's pretty weird since Server is the next step up from Player.  As far as a reliable XP VM is concerned, did you try building it in VMWare Server?  I only ask because I did and haven't had any trouble with any of my apps, so I'm curious to learn more.  I haven't tried accessing my scanner yet - might try that later tonight to see what happens.  It is USB 2.0 as well, so I'll get a chance to see if there is any problems.  Really curious about all of this and would like to find out the "whys" if you know what I mean:)  Please post back any additional information, and I'll go try my scanner.:)

---

### Post by Gary.M on 2007-08-11
Hi, well I had a VM that was hardware level 3 or 4  (pre workstation 6) and it was running under the player that the repositories install... no way would anything that was USB work with any sort of useful performance. I moved to Player 2. Had the VM upgraded by Workstation 6 so the hardware now included USB 2.0. Now under player 2 which supports USB 2.0 and workstation 6 machines I can use the USB devices with almost full USB 2.0 speeds. I don't think the server product supports USB 2.0, its just USB 1 isn't it?

---

