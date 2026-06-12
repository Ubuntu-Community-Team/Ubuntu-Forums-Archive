---
title: "How to install 9.10 on a MacBook?"
date: 2009-11-09
forum: Apple Hardware Users
---

### Post by vibe3 on 2009-11-09
Hi all,

  I've been looking through the various threads with all the problems involved in installing Karmic 9.10 on a MacBook. Could someone post comprehensive instructions on how to do this on a clean MacBook install? I was searching through some threads which seem to have bits and pieces of info, but the official help page:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

has been "under revision" for a while now and I can't seem to find some simple easy to follow instructions.

---

### Post by groovete on 2009-11-09
Confused, because the website with a detailed howto is online!

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by vibe3 on 2009-11-09
> **groovete said:**
> Confused, because the website with a detailed howto is online!

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Yes but that does not seem to be updated for 9.10 which switches to the new grub2 boot loader. I've read some threads of people saying that rEFIt breaks things in 9.10 etc.

---

### Post by ColdLunch on 2009-11-09
Don't install rEEFIt.  You don't need it.

Pop in the Ubuntu Live CD.
Partition your drive with gparted.  
Start installation.
On last screen of installation, hit "Advanced".  Set grub to dev/sda/1.
???
Profit.


Thats what I did and it works great.

---

### Post by Who on 2009-11-13
> **ColdLunch said:**
> Don't install rEEFIt.  You don't need it.

Pop in the Ubuntu Live CD.
Partition your drive with gparted.  
Start installation.
On last screen of installation, hit "Advanced".  Set grub to dev/sda/1.
???
Profit.


Thats what I did and it works great.

Did you keep OS X?

---

### Post by zAfi on 2009-11-16
I did it the same way as ColdLunch but installed grub on my /boot partition (sda3 in my case). After syncing the partition table with a rEFIt disc I can choose what I want to boot by holding the option key.

---

### Post by aprigiosimoes on 2009-11-16
no problems efi with grub2.

[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

---

### Post by ian_hawdon on 2009-11-16
I haven't had a problem with grub2 and rEFIt, apart from it thinking it's a legacy OS, so the Tux icon doesn't appear!

Does using grub2 for EFI make (k)ubuntu perform any better then the current method (which seems to be a PC BIOS emulation)... if so, how do I convert my current setup to use Grub2 instead of rEFIt?

---

### Post by _mario_ on 2009-11-16
> **ian_hawdon said:**
> I haven't had a problem with grub2 and rEFIt, apart from it thinking it's a legacy OS, so the Tux icon doesn't appear!


same for me. but that's not a big problem...

> **ian_hawdon said:**
> 
Does using grub2 for EFI make (k)ubuntu perform any better then the current method (which seems to be a PC BIOS emulation)... 


depends on the flavour. the PC variant of grub2 (that is beening used by the install disc) also causes the EFI firmware to enable BIOS emulation.

the EFI variant must be installed explicitly to the efi-folder of OSX's system partition to be used, and afaik, since no BIOS emulation is enabled, some drivers, in particular the proprietary Nvidia driver, refuse to work (at least when i tried the last time).

> **ian_hawdon said:**
> 
if so, how do I convert my current setup to use Grub2 instead of rEFIt?

this is not advisible at all. but you might convert from grub1 to grub2: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2).

ciao,
Mario

---

### Post by aprigiosimoes on 2009-11-16
problems?

install ubuntu and then enter the live cd of ubuntu open console and mount the partition that ubuntu is installed and use chroot to enter the partition.

mount / proc and install grub 1 (grub or grub-legacy) and run grub-install / dev / HARD OR update-grub

and reboot.

---

### Post by ian_hawdon on 2009-11-16
@_mario_

Grub2 was installed by default with Karmic, was just wondering if grub2-efi gave any performance boosts. They say that the Intel video card should work with the efi grub, but it doesn't look like there are real reasons to mess around with a working system!

I'll stick with the "if it ain't broke, don't fix it" method for now!

---

### Post by richard.campbell.vancouve on 2009-11-16
I strongly recommend not using dual boot technologies, they are not needed for any dual-core MAC.  I am using 9.10 on my iMac running Snow Leopard (for the enhanced 64 bit support) no problem. In fact I am using it right now.  I have now installed it four times in two different kinds of setups and I will explain them below.

I use sun.com's VirtualBox (free) and currently the 64 bit version of Karmic.

Download **VirtualBox-3.0.10-54097-OSX.dmg**  from Sun, and install. 

Download and save to a location on HD the following iso files:

a) Just to try up the basics set up, **ubuntu-9.10-desktop-i386.iso**

b) To get the enhanced 64 bit speed and functionality, **ubuntu-9.10-desktop-amd64.iso**

c) And if you want even more speed using a raid0 setup,**ubuntu-9.10-alternate-amd64.iso**

You could download run the Ubuntu server if you wanted to explore that too.


1. 32bit 9.10 on a 20GB drive.  Launch VirtualBox and click New. Choose O/S Linux and version Ubuntu. Assign 1/3 of your RAM to it.  Assign a dynamic 20 GB drive (starts as about 10 MB and grows as you add files), opt for install from CD, point the installation CD to the ubuntu-9.10-desktop-i386.iso

Then, before you launch the virtual machine, edit the properties (these are same for all instances):  2 CPUs; 128MB video ram; enable additional controller--change your assigned drive from IDE to SATA port 0; disable 3D acceleration; remove the floppy from the boot order and make it CD, HD

Run the Virtual machine and install Ubuntu as normal in regular a app-window on your MAC desktop (you will fix the small screen after installation). 

Shift your brain at this point, from within the virtual window, Ubuntu is unaware that it is just a big fat file and acts as if it had a real HD, keyboard drivers & etc.  So now when I say save a file to your HD or format a drive, I mean from within the virtual Ubuntu, to its HDs.

Do ALL the upgrades you can, especially kernel upgrades.  Eject the CD-ROM from the Ubuntu desktop or from the bottom right edge of your VBox app window, the CD icon. Then reboot the Ubuntu from its own menu.  Lastly from the VBox menu on your MAC, install additions.  Note:  It works better if you copy the virtual CD that pops up on your Ubuntu desktop to a folder on your Ubuntu machine and run the appropriate VBoxAd[....].run script from within a root terminal.  Then reboot the Ubuntu from its own menu. When you are logged in, toggle the left Command-'f' key combo, and you will be in a full screen ubuntu session.  I prefer the Seamless mode where both Ubuntu windows and Mac windows co-exist on my Mac desk top, but that is your choice.  Hint: You may need to re-install the Vbox addition after any kernel upgrade, so that is why I save the files to a directory on the Ubuntu machine.



2. 64bitcomputing on your Snow Leopard MAC.  Almost identical to the 32 bit mode but change/add the following: Linux OS and ubuntu64 for your new machine.  Point to the  ubuntu-9.10-desktop-amd64.iso for your install media. In the settings before launching, enable VT-x/AMD-V and Nested Paging. 



3. Fast 64 bit with raid0.  By now you should be comfortable with the basics of installing a VBOx Ubuntu.  The pattern for this follows the other 64 bit with the following changes. Launch VBox first without a machine. Press command-d and create four 5GB virtual drives, appropriately named.  Now start creating your 64bit machine, but instead of creating a new drive, assign the first of the four you just made to it.  You will add more later. Use the  ubuntu-9.10-alternate-amd64.iso  as your install media.  Make all the changes in machine settings as above adding the four created drives in turn as SATA ports 0 through 3.

Start the machine and install.  When you get to the partitioner choose Guided. The next bit is a little tricky, but it is the same action 4 times.  First, partition the first drive.  Create two logical partitions on it:   5.1 GB raid0 and 2.88 mb extended.  *Formatting: note, you will be using less secure file systems for speed, but remember, the actual "HDs" are ordinary files on your excellent MAC so error correction in mostly redundant here.*  Format the two logical partition as Ext2 mounted as "/" and Swap respectively.  Make the SATA disk bootable.  

Repeat this exactly for all your SATA drives.  Them, make the four 5.1 GB disks your first raid set, the four swap disks your second raid set Complete your installation using raidset-0 as your system disk partition, and raidset 1 as your swap partition.  Continue as above for post install and finally VBox additions. You're ready to fly


----
Thoughts: 

This method is the same as installing Ubuntu server with a raid configuration.  You could start the server install and abort it after creating the raid and then go back and do it with the desktop iso file (which is what I did my first time), but using the alternative iso cuts out a step.  

In theory, if you want to play with raids, you could create any number of empty raid sets of any flavour or size you want of dynamic virtual drives and archive them for future use, they only take a few MB of disk space until you actually use them.  If you want max speed on extensive virtual diskspace-used file ops, use fixed-sized storage disks, but they will be full-sized files on your MAC HD even when empty of virtual content and, if your virtual content remains below about 10-15GB, they would actually be slower.

Speculation here:  If you were to create a raid5, you might be able to "kill" a disk and "replace/restore" it, with the advantage that the general slow irreversible swelling of dynamic virtual disks to max size might be reset to as small as possible.  I am not sure where the bootsector is stored in a raid of multiple bootable logical drives, but if it is also striped, even SATA 0 could be "killed and restored.

---

### Post by ColdLunch on 2009-11-16
> **Who said:**
> Did you keep OS X?

Yes, I kept OSX.

If you have questions, PM me. I will try and help.

---

### Post by jamesey on 2009-12-10
i have a fresh install of osx on my new imac. what is the foolproof way to

1. make my machine boot to karmic
2. keep a small 20gb OSX partition

some people say i need refit
some people say i dont

---

