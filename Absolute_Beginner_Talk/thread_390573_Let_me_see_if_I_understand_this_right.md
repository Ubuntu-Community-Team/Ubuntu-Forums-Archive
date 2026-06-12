---
title: "Let me see if I understand this right"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-03-22
If I install Virtual Machine, do I install windows as the virtual OS?. If so will I then be able to run the few programs there are not equivalents to in Ubuntu? I am still rather new to Linux and the question may have answered before.

---

### Post by arkangel on 2007-03-22
true

---

### Post by energiya on 2007-03-22
> **J11Gyro said:**
> If I install Virtual Machine, do I install windows as the virtual OS?. If so will I then be able to run the few programs there are not equivalents to in Ubuntu? I am still rather new to Linux and the question may have answered before.

When you start Windows with WM you will be able to open programs like you would in win. The only limitation is hardware related (wm emulates hardware).

---

### Post by J11Gyro on 2007-03-22
Ok so I can run, for instance Win 98SE kinda like a program then run bryce and poser in that environment and import images into Gimp while both os's are running? What is WM?

---

### Post by energiya on 2007-03-22
> **J11Gyro said:**
> Ok so I can run, for instance Win 98SE kinda like a program then run bryce and poser in that environment and import images into Gimp while both os's are running?
It will be something like making a new login in a nested window.
**edit:** you will be able to import things if you first save them to fat32 or any partition or media that can be accessed by both linux and win running in a virtual enviroment.

> **J11Gyro said:**
> What is WM?
I was thinking about wmware. But there are other virtualization apps like qemu or virtualbox.

---

### Post by J11Gyro on 2007-03-22
Do you have a sudo command for install o everything need to do this or a link where I can try and get info to make this work. Will XP work also?

 Machine info
AMD XP 2400 1.5 gig ram , nvidia 5200 128m video card and SB live

---

### Post by energiya on 2007-03-22
Your specs are good so WinXP should work just fine. Try searching the forums for wmware, qemu or virtualbox. There are a lot of nice tutorials on how to configure all ;)

---

### Post by HereInOz on 2007-03-22
Here are the instructions for installing VMWare server on Ubuntu.  They are not mine -  but I cannot remember who posted them, but whoever it is, they deserve all the credit.  They relate to Dapper, but I believe the process is the same for Edgy.

================================================

Are you too having problems with software that is only available on Windows and not on Linux? Are you still Dual Booting to solve this problem? After this HowTo you will never need to dual-boot again for your windows only software, like Adobe CS!


Info
That sounds great, but how?
Did you ever heard about Virtual Machines? There is software available that can run Windows XP or any other Operating System inside your main Operating System. This means that you can run Windows XP in Ubuntu without the need to Reboot/Dual Boot. 

That sounds slow...
It is indeed a little slower, but really: a little. Personally I am very willing to sacrifice that little speed in order to avoid Dual Booting.

What else can I do with it?
Run seperate Operating Systems for Online Banking and other things that you want to secure. Try out new Ubuntu Versions without Dual Booting, Try out other Linux Distro's etc. 

What can I not do with it?
You will not be able to use hardware that doesn't work on Ubuntu. This is very important to understand!
The Virtual Machine runs on top of Ubuntu, so it can only acces Ubuntu detected devices. It is a virtual machine with virtual hardware. 

Also don't expect to be gaming on a Virtual Machine at this moment. Heavy Videocard 3d things are just not supported right now. So for gaming it's unfortunately a no go. For everything else, just try it out!


Requirements
Ubuntu Dapper or Breezy
A Windows XP Installation CD & Key
Internet Connection (+- 100 Megabyte file download)

Procedure 
First we need to install a few dependencies:

In a terminal type
Code:
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
This will install all needed dependencies (atleast I hope so  )

Breezy users will also need to install gcc-3.4. 
Code:
sudo apt-get install gcc-3.4

We are now ready to download VMWare Server.
Go to [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
On the menu on the right click: Download VMWare Server
Click on the appropriate Download Now button.
Register as new user, do give a valid email adres, since you will be receiving the registration key by email.
Select the VMWare Server beta (for Linux)
Accept the EULA
Download VMware Server for Linux. (first mentioned, binary (.tar.gz) )
The Installation
Open the downloaded file with the archive manager.
Extract it to somewhere, I will use /tmp here.
Startup the terminal and go to the extracted files 
Code:
cd /tmp  replace with your download directory
cd vmware-server-distrib
Breezy users only. Execute 
Code:
export CC=/usr/bin/gcc-3.4
Execute the installation script 
Code:
sudo ./vmware-install.pl
You can accept all defaults, only thing you might want to alter is the directory where the Virtual Machines are stored. I have mine set to /home/username/vmware . But offcourse, just accept the settings you want to.
You will be prompted for your key during the installation. You will find the key in your email inbox
If everything went allright, the installation will finish without any problems
We can now test if it worked by starting the VMWare server console
Via the menu Applications => System Tools => Vmware Server Console
If everything is allright, the server console program will show up.
If it didn't, start the terminal and execute 
Code:
vmware
This will display the errors, post them here and hopefully we can solve them.
Next thing we want to do is Install Windows XP !

First we need a virtual machine
Insert your Windows (XP) CD into your CDROM drive
Open the VMware Server Console
select 'Create a new virtual machine'
=> Next => Next => Select Windows Xp (or whatever Windows versions you want to install )
=> Next => Enter a name and select a location for the Virtual Machine File (It contains the virtual harddisk, so it needs quite some space, min 2 GB, but I would recommend 8+ GB )
=> Next => Select Network type. I am using NAT, but choose whatever fits you ( or your mood )
=> Next => Choose the size for the Virtual Disk and set other preferences
=> Next => Finish
Now we can start the newly made virtual machine and the install of Windows!
Start the virtual machine
Hopefully it detects your Windows install CD and will start the installation! If it won't boot from the CD, stop the virtual machine and check/change the preferences for the virtual machine regarding the CD drive
Enjoy the installation and the freedom to use Ubuntu while installing 

Tips

You will definately want to install the VMWare tools, when windows has been installed. This will speed up your Windows responsiveness 
Make sure your Windows Virtual Machine is Running and visable/selected. (Not in FullScreen)
Go to the VM menu (on the top in the VM Server Console)
Select Install VMWare Tools. 
This will start a installation wizard in your WIndows Environment. Just install the stuff and you will have better mouse and system responsiveness.
CTRL + ALT will release the mousecursor from the virtual machine
CTRL + ALT in FullScreen mode will get you out of the FullScreen.

You can Suspend a running virtual machine. this way it will start very fast the next time you need it.

To have sound support, add a sound device in the virtual machine settings.

Enjoy!

See Attached screenshots from my windows XP Installation and the succes of it.

Please no discussions about Windows versus Linux in this Thread.


Common Problems & Solutions
No Serial Number Received
You can view your serial numbers at: [http://www.vmware.com/vmwarestore/ne...mber_login.jsp](http://www.vmware.com/vmwarestore/ne...mber_login.jsp)
After a kernel upgrade VMWare won't start because it has not been (correctly) configured for the running kernel
execute 
Code:
sudo /usr/bin/vmware-config.pl

vmware-config.pl fails to find the right kernel headers. It cannot find /usr/src/kernel/include and won't proceed to install.
You have a updated kernel, but not the updated kernel headers. 
You can install them by executing 
Code:
sudo apt-get install linux-headers-`uname -r`
Now you can succesfully run 
Code:
sudo /usr/bin/vmware-config.pl

You don't want to install the kernel headers manually each time there is an update.
There is a package called linux-headers-*** that automatically installs the latest kernelheaders, so you don't need to install them manually each time.

There are 4 flavours of this package: 386, 686, k7, server.

If you don't know wich one you need, execute 
Code:
uname -r
It will give you something like 2.6.15-26-k7 or 2.6.15-26-686

Now you know the right flavour, install it by 
Code:
sudo apt-get install linux-headers-***
Replace the *** with 386, 686, k7 or server.
Uninstallation failed and reinstall won't work 
====
A previous installation of VMware software has been detected.
The previous installation was made by the tar installer (version 3).
Keeping the tar3 installer database format.
Error: Unable to execute "/usr/bin/vmware/vmware-uninstall.pl.
Failure
Execution aborted.
====
Look for the /etc/vmware directory and either move it to a different location or remove it altogether. 
Code:
sudo rm -R /etc/vmware

Note
According to Flip314: 
Quote:
VMWare has stated that VMWare Server will be a free product, just like VMWare player. 



Credits
Used some information from a blogpost by James Wilford and a comment placed there by 'mips' ([http://blog.wilf.me.uk/articles/2006...beta-on-ubuntu](http://blog.wilf.me.uk/articles/2006...beta-on-ubuntu) )
Thanks to Remusus for the linux-headers-'uname -r ' command.
Thanks to firetux for the GCC-3.4 info
Thanks to Nick Couchman from the VMWare forum for the uninstallation problems workaround.

---

### Post by J11Gyro on 2007-03-22
Thanks I will give it a shot, I would love to be totally away from Windoze. Thanks again.

---

### Post by J11Gyro on 2007-03-23
Ok have tried all the scripts and do just fine till install, it says another version has already been installed, if i can find it how do i remove it?

---

### Post by J11Gyro on 2007-03-23
here is the error i am getting on install

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.
  anyideas?

---

### Post by J11Gyro on 2007-03-23
Ok finally got it working :guitar:  now just to install windows 98SE from upgrade disk :lolflag: Thanks for the help, that is truly what I like about this community

---

### Post by J11Gyro on 2007-03-23
Does anyone know how to correct this error?

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

---

### Post by HereInOz on 2007-03-23
When does it happen?  Never seen it so can't really offer much, but if you tell us when it occurs someone might come up with a solution.

---

### Post by J11Gyro on 2007-03-23
After install completed I rebooted and tried to open Virtual Console and sys locked up so I ran this sudo /usr/bin/vmware-config.pl and got that error code

---

### Post by J11Gyro on 2007-03-23
Ok now another dumb question, how can I uninstall VMware totally and start over?:)

---

### Post by Bachstelze on 2007-03-23
have you ried the bin/vmware-uninstall.pl script ?

---

### Post by J11Gyro on 2007-03-23
yes tried that and still remnants remain wasting space:confused:

---

