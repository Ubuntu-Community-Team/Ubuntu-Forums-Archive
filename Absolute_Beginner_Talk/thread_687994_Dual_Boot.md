---
title: "Dual Boot"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by wwhwd on 2008-02-04
I would like to know if it is possible to have a dual boot system with Vista and Ubuntu. I looked at Xandros and that program took over vista. Long story short I had to reformat and get vista back on as I am unfimiliar with Linux programs. I would like to learn but in the mean time I still have to use vista.
Thanks

---

### Post by LaRoza on 2008-02-04
Yes, it is easy now

[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

(I have done is several times with no problems)

---

### Post by kool_kat_os on 2008-02-22
ya....its REAL easy:)

---

### Post by jan quark on 2008-02-24
check out this site too

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by -random on 2008-02-24
Yep real easy!

I only had one issue:

Vista might give you some trouble about 'requirments not met' when choosing a install partition.

If this happens>>
 Simply boot from the live cd, and make the ntfs partition you want to install Vista to 'boot' (run 'gparted' from terminal, right-click on partition, then manage-flags > click on 'boot')

---

### Post by Dr. Koncar on 2008-03-03
Scenario: You want the simplest way to dual-boot Vista and Linux. You've already installed Windows Vista and now want to dual-boot it with Ubuntu 7.04
Summary of tutorial: This is an updated tutorial - we previously used Ubuntu 6.10 and then modified the GRUB bootloader to force Ubuntu to recognise the Vista partition. In this tutorial, we'll use Ubuntu 7.04 which does a much better job in interacting with Vista. We'll use the Vista management tools to resize the main partition and install Ubuntu into the freed space.
This tutorial has been tested on a VMWare Workstation 6 machine and an ASUS P5AD2-based Intel system with 2GB RAM and an 80GB Seagate SATA drive.
Get started

Boot into Windows Vista and go into Disk Management - right-click My Computer, Manage, Disk Management.

Vista Disk Management
 
 
Right-click on the main Vista partition and select Shrink Volume

Vista Disk Management - Shrink Volume

 
The Shrink tool will assess how much space can be freed up.

Vista Disk Management - Shrink Volume 2

As a rule of thumb Shrink will reduce the main system partition by about 50%. As long as the partition is big enough to begin with (at least 10GB) it should accommodate both operating systems.
Select Shrink and the tool will reduce the volume of the primary partition, leaving the rest of the disk free as unpartitioned space.

Vista Disk Management - Shrink Volume 3

 
Once that's done, shut down the Vista machine.
 
Install Ubuntu

You'll need the latest desktop ISO of Ubuntu (7.04). You can choose a list of download mirrors from the Ubuntu website, or use this link from Planetmirror. Download the ISO and burn it to CD to create an Ubuntu Live CD.
Boot the Vista machine from the Live CD and select "Start or install Ubuntu".

Vista & Ubuntu - Install Ubuntu

 
Once the Live CD has loaded, double-click the Install icon on the desktop to start the installation process.
On the Welcome screen, choose your language and select Forward.

Vista & Ubuntu - Install Ubuntu - Language
On the "Where are you" (timezone) page, select your location and then Forward.

Vista & Ubuntu - Install Ubuntu - Timezone
 
On the next screen, choose the appropriate keyboard layout and then Forward.

Vista & Ubuntu - Install Ubuntu - Keyboard

 
Ubuntu will then load the disk partitioner to determine where it's going to be installed. Choose "Manual - use the largest continuous free space". This will automatically select the unpartitioned space we created earlier using the Shrink tool. Click Forward.

Vista & Ubuntu - Install Ubuntu - Disk Partitioner

On the Migrate Documents and Settings screen, if Ubuntu finds any user accounts to migrate, feel free to import it from Vista to Ubuntu. If it doesn't find any, obviously this isn't an option. Click Forward.

Vista & Ubuntu - Install Ubuntu - Migrate

 
On the "Who are you?" screen, enter your username and password details, then click Forward.

Vista & Ubuntu - Install Ubuntu - User Details

 
On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". This means that regardless of whether Ubuntu found any user account to migrate, it certainly knows that Windows Vista is installed on the other partition and is aware of it. Click Install.

Vista & Ubuntu - Install Ubuntu - Install

 
See the install through and then let it boot into Ubuntu.
When the install is complete the system will reboot. When the GRUB boot menu is displayed, have a look at the last entry in the list.

Vista & Ubuntu - GRUB Bootloader

After the Ubuntu boot options, there will be an entry “Other operating systems” and beneath that "Windows Vista/Longhorn loader”. By default Ubuntu will load itself after 10 seconds, but you can select the Vista option and Vista will boot normally.
 
Configure GRUB

If you want to modify how GRUB handles the new dualbooting environment, you need to edit the boot menu. Boot into Ubuntu and open up a Terminal window (Applications, Accessories, Terminal), and type in:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
and enter your root password when asked - this makes a backup of the GRUB menu file just in case things go wrong.
Next, type in:
sudo gedit /boot/grub/menu.lst

Dualboot - Configure Boot Menu

 
This opens up the boot menu as a text file in gedit.

Dualboot - Boot Options

 
There are loads of options you can change, but only a couple that you’re likely to be interested in. The default boot entry is defined by the “default” value.
The default value is 0, which means that the first entry in the list (which is Ubuntu) always gets loaded.
If you want to make it so that Windows Vista loads by default, change the value to 4, as Vista is the fifth item in the list (the numbering system starts at 0 and "Other operating systems" counts as a line).
The other way to load Windows Vista by default is to change the value for “default” from a numerical value to “saved”. Then, GRUB will load whichever boot entry has been marked with “savedefault”.
If you scroll down the list and have a look at the entries, you’ll notice that both the main Ubuntu entry and Windows Vista have been marked with “savedefault”. Remove the value for Ubuntu and Windows Vista will launch by default.
It's also worthwhile changing the description of the Vista entry from "Windows Vista/Longhorn (loader" to just "Windows Vista".
You can also increase the boot menu timeout – just change the value for “timeout”. You can also hide the GRUB boot menu by removing the hash in front of “hiddenmenu”. Save and exit gedit to keep any changes.
If instead of GRUB you want Vista's bootloader to be in charge, load up the Vista installation and install EasyBCD. Go to “Manage Bootloader”, then “Reinstall the Vista Bootloader”, an GRUB is overwritten. You can then configure the Vista bootloader to add Linux to the boot menu.

---

### Post by jyesj on 2008-03-16
I really appreciate of this post. But I would like the same for window XP. one more question I'm using dell machine and operating system is windows xp i want dual boot with complete safety of windows xp system and data. I  have 4 partions while partion C is my primary dos is 5 GB and reamining 35 GB in E, F, G while my Cd rom is D. If in the future i want to remove ubuntu from system without disturbing windows xp is it possible. (i hope i will not) please guide me my email is [email]jyesj@hotmail.com[/email]

---

### Post by bodhi.zazen on 2008-03-18
There is a guide on these forums :

Remove Ubuntu (Restore Windows):

	[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

