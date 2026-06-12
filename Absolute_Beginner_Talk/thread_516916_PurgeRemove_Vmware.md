---
title: "Purge/Remove Vmware"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Vanish00 on 2007-08-03
I wanted to try and install VMware using this guide ([http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)).  Now I found another way to install the VMware but now I can't install it using ubuntu geek because now it detects another one.  How do I uninstall/remove/purge the old one from my system?

---

### Post by HermanAB on 2007-08-03
Easy, hunt it down with 'find' and delete it without mercy:
$ sudo find / -name vmware*

BTW, in my experience, the easiest way to install vmware, is to download the archive from the vmware web site and run it.  They created this thing, and they seem to know how to install it...

Cheers,

Herman

---

### Post by cwmoser on 2007-08-03
I've removed and installed VMware several times and these are my notes that I have gleaned from various posts.  Note also that I have notes to resize a virtual partition.

Carl



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




Troubleshooting

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) 

The file I downloaded was vmware-server-distrib.

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
sudo rm -r /etc/vmware

apt-get remove --purge vmware-server


Apply Patch:
[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

VMware-any-to-any-update patches 
Posted: Oct 30, 2004 3:05 PM 
 

Reply 

You can redistribute or translate text below as you want, in whole or in part, as long as it is clear that I wrote it. You can also fix grammatical errors during redistribution. Semantic modifications are not allowed without special permission. 

======================================================== 

What is vmware-any-any-update ? 

First, if you rely on support from VMware, or you are paying for it, just stop reading here. Unless VMware support told you to download that file and gave you instructions how to apply it, then DO NOT APPLY it. VMware support will not help you if you are running on unsupported host, and I'll not help you either. Now, if you can help yourself, you can continue reading. But you have been warned. 

If you find that VMware, VMware Express, VMware Workstation or VMware GSX Server does not work on your Linux host, it is probably time to upgrade your VMware software. So before doing anything make sure that you are using latest product available for your license: VMware 2.0.4, VMware Express 2.0.4, VMware Workstation 3.2.1, VMware GSX Server 1.0.3, VMware GSX Server 2.5.1, VMware Workstation 4.5.2 or VMware GSX Server 3.1.0. Maybe it will fix problem for you, and you'll not have to apply vmware-any-any-update at all. It is especially important to upgrade from WS 3.2.0 to WS 3.2.1. 

If you have still problem with building kernel modules, or if VMware application refuses to run complaining that your kernel is too new, it is time to download this patch. You can find latest version of patch at [http://platan.vc.cvut.cz/ftp/pub/vmware](http://platan.vc.cvut.cz/ftp/pub/vmware) , or at its mirror [ftp://ftp.cvut.cz/vmware](ftp://ftp.cvut.cz/vmware)

Filename of patch has form "vmware-<product>-<version>-update<sequence>.tar.gz" where <product> is currently "any" (it was ws/gsx in past; maybe it will be host/tools in future), <version> is currently also "any" (it was build number long ago when patch was not that universal), and <sequence> is just number starting at 1 and incremented with each release. 

Download newest file which matches system you are using: currently it is simple, just grab latest vmware-any-any-update*.tar.gz file you can download. 

After downloading unpack file into some directory, enter that directory and run "./runme.pl". After doing that run "vmware-config.pl", or, if you installed update on system which is supported by your product (though I do not understand why you installed product in this case) "vmware-config.pl -compile". Note that while original modules from VMware do not need C++ compiler, my updates need it, and won't build without - it is price I had to pay to get support for all these products from one source. 

After that your kernel should not complain about problems with kernel modules anymore, and everything should run as on supported host. 

And some general advices: if you are having problems with starting your '99 product on your '04 distribution, you should try 'LD_ASSUME_KERNEL=2.2.20 vmware' instead of pure 'vmware'. And make sure that your /tmp filesystem is not mounted with 'noexec' and that you have sufficient space there (several gigs at least). 

That should be everything needed. If you want to know what really changed between releases, you can download older versions of patch from 'obsolete' subdirectory of [http://platan.vc.cvut.cz/ftp/pub/vmware](http://platan.vc.cvut.cz/ftp/pub/vmware). It contains all updates I ever released - since first one, which is more than 5 years old. 




If you get the "error exit status 1", then do this:
Edit /var/lib/dpkg/info/vmware-player.postinst and add a line "exit 0" to the top. The next time, apt-get runs, it will skip the buggy postinst script, believe that VMWare is successfully installed, and update its database.

If you get error exit status 10:
E: /var/cache/apt/archives/vmware-player_1.0.2-2_i386.deb: subprocess pre-installation script returned error exit status 10
Do the following:
sudo apt-get clean
sudo apt-get update


Virtual Machines stored at:
	/var/lib/vmware/Virtual Machines/Windows 2000 Professional


Applications -> Other -> vmware

vmware 
Next thing we want to do is Install Windows (XP) !

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

Applications -> Other -> vmware


Sound Issues:
Did you import this VM using VMware Converter or is this a fresh XP install using Windows Easy Install? 

If you check in Windows Device Manager, can you check to see if sees a sounds card at all and if so is there a driver for it? 

If you used VMware Converter to bring this computer into a VM, the sound card may be incorrect. You can try the following: 

1) Shut down and power off the VM 
2) Go to Settings and select the sound adapter, click the minus button at the bottom of the sheet to delete the sound adapter 
3) Click on the Plus button and select add Sound adapter and click Apply 

Power on the VM and try sound in this case. 


 

I am using vmware-server-1.0.1-29996 because

it is free. You stiill have to register and get a serial #.

From what i understand vmware-workstation

is a demo which expires in 30 days.

 

To do the install i added in /etc/make.conf

VIDEO_CARDS="nv nvidia vmware"

This will install vmware video driver on your

WinXp "guest" when you install the vmware tools

on the guest, while logged in from the host.

I then did the install and used all defaults

on config questions. After install i followed the

instructions from FranzRogar.

1 - VMWare -> View

[ ] Autofit window

[X] Autofit guest

 

2 - VMWare -> Edit -> Preferences -> Display

Autofit

[ ] Autofit window

[X] Autofit guest

 

3 - VMWare -> Edit -> Preferences -> Input

Keyboard and Mouse

[X] Grab keyboard and mouse input on mouse click

[ ] Grab keyboard and mouse input on key press

 

Cursor

[ ] Grab when cursor enters window

[X] Ungrab when cursor leaves window

[ ] Hide cursor on ungrab

 

4 - VMWare -> View

[ ] Favorites

[ ] Status Bar

[ ] Tabs

 

5 - VMWare -> View -> Toolsbars

[o] Selective text beside icons

 

6 - Virtual machine -> View Settings -> Options

Power

[x] Power on after opening this virtual machine

[ ] Enter full screen mode after powering on # your start script will handle this

[x] Close after powering off or suspension


/var/lib/vmware/Virtual Machines

vmware-config.pl scritp to make network changes to the host
$ vmware-vdiskmanager.exe  -r  sourceDisk.vmdk  -t0  destinationDisk.vmdk

$ vmware-vdiskmanager.exe  -c  -s8GB  -a lsilogic  -t2  myscsiDisk.vmdk


Expand disk – then you need to resize the partition:
This will resize the HD but not the partition:
	$ vmware-vdiskmanager  -x16Gb  “Windows 2000 Professional.vmdk”
Download a copy of BootIt NG (Boot It Next Generation). [http://www.terabyteunlimited.com/downloads/bootitng.zip](http://www.terabyteunlimited.com/downloads/bootitng.zip)
Run the .exe to create an ISO image file:  BOOTITNG.ISO
Make sure and include the VGA drivers in the options.
Create a CDROM from the BOOTITNG.ISO image:  
Boot the BootIt ISO image CDROM in the Virtual Machine.
Hit ESC to get the Boot Manager.
When the BootIt GUI starts, don't install to hard drive.
Resize the Partition.
Restart the Virtual Machine.

NOTES:  Use BootITNG CDROM to resize the vmware partition – GPARTED will not work.
	You might have to CHKDSK the partition if BOOTITNG detects an error.

---

### Post by Gary.M on 2007-08-03
I've been through this recently, and I'd recommend Vmware Player V2 from the tar install obtained from Vmware's site. In their docs section get the user guide pdf and follow that. When installing just accept all the defaults.

First though, comment out any extra kernel versions from your grub menu.lst. That way the install will compile the right stuff first time.

Find yourself a suitable appliance to run, or create your own machine at easyvmx.com

Install your OS in it.

I have WinXP running under Kubuntu Feisty. I have access to USB2 devices - scanner, removable NTFS USB drive... etc. (I don't think the current version of Vmware server supports USB 2) I use Samba shares on my host and map those within the XP guest. Its bullet proof and works really well.

Oh, you'll want to install the Vmware tools too for it to run at max speed.

---

### Post by wak_wak on 2007-08-19
That's a lot of data so forgive me for not reading it all.  But try this:

I was having the same problem and ran in to various others after spending a couple of hours trying various solutions.

Ultimately I went here: [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

That totally got it up and running.

The only thing I had to change was that where it says to command: sudo vi /etc/apt/sources.list

I changed "vi" to "gedit".

Make sure to go to vmware.com and get a license.

You'll love it once you've got it up.  I used it a bit under Windows before and it's an amazing tool.

If you've tried to install it, unstall 1st:  sudo vmware-uninstall.pl

---

### Post by indiechixor on 2007-10-16
I'm also attempting to remove Vmware with the hopes of installing it correctly (i had it in my mind to use Automatix....stupid me)

I've come across this stumbling block: 
```
root@Hikaru:/home/indie/vmware-player-distrib# ./vmware-install.pl
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmmon
vmnet

Execution aborted.


```

I've located said files, and attempted to remove them, but with no avail.
I logged in under root, changed all the permissions to 777, and they STILL will not allow me to delete them.  I keep getting the ```
 rm: cannot remove `/sys/module/vmmon/': Operation not permitted 
``` error.

I've tried everything in my brains to delete these files, but to no avail. I have all the permissions, i use sudo rm -r, rm -r, and physically deleting them... nothing.

HALP :(

---

### Post by marcellosales on 2008-01-17
I have a workaround... Change the following line of the /usr/bin/vmware-config.sh

From:
if (scalar(@modules) > 0) {
To: 
if (scalar(@modules) == 0) {

Then, proceed with the installation/configuration again... I did run the uninstall and install again... This will enable the modules again... After the reinstallation of the modules, the installation will fail again and you just change the configuration back to how it was...

It worked for me... :guitar:

---

