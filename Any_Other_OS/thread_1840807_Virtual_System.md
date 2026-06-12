---
title: "Virtual System"
date: 2011-09-08
forum: Any Other OS
---

### Post by avi k on 2011-09-08
I have a computer with Windows 64 bit
 I want to install a virtual system of Fedora on windows, I am looking for a site where you can download the Fedora 64-bit version of VMware and 64-bit, does anyone know a site where you can download these versions?.
 And Question: Does anyone know a package ready which included the VMware and Fedora, so I do not have to install them separately?.

---

### Post by haqking on 2011-09-08
> **avi k said:**
> [SIZE=3]I have a computer with Windows 64 bit
 I want to install a virtual system of Fedora on windows, I am looking for a site where you can download the Fedora 64-bit version of VMware and 64-bit, does anyone know a site where you can download these versions?.
 And Question: Does anyone know a package ready which included the VMware and Fedora, so I do not have to install them separately?.[/SIZE]


You dont download a 64 bit version of fedora vmware.

You download the virtualisation software of yoru choice be it Vmware or[ Virtualbox]("http://www.virtualbox.org"), i personally prefer [Virtualbox]("http://www.virtualbox.org")

Then install whatever OS you like to virtualise.

In the case of [fedora]("http://fedoraproject.org/en/get-fedora-options") download the .iso here from [Fedora]("http://fedoraproject.org/en/get-fedora-options") 

And then use that .iso  in your virtualisation VM to install.

---

### Post by howefield on 2011-09-08
Thread moved to "*Other OS/Distro Talk*"

---

### Post by avi k on 2011-09-08
Thank you

> You download the virtualisation software of yoru choice be it Vmware or[ Virtualbox]("http://www.virtualbox.org/"), i personally prefer [Virtualbox]("http://www.virtualbox.org/")

Is there a guide that explains step by step how to install the virtualbox?.

---

### Post by haqking on 2011-09-08
> **avi k said:**
> Thank you

[SIZE=3]
Is there a guide that explains step by step how to install the virtualbox?.[/SIZE]


Yes, always read the links people post.  Documentaion, downloads, instructions etc are all there.  See here specifically [http://www.virtualbox.org/manual/ch02.html](http://www.virtualbox.org/manual/ch02.html)

---

### Post by avi k on 2011-09-08
Thank you.

 I will look for a guide how to install Fedora on the virtualbox.I hope there is a guide.

 Thank you

---

### Post by Johnb0y on 2011-09-08
old one: 

[http://www.fliquidstudios.com/2009/03/19/installing-fedora-10-on-windows-xp-using-virtualbox/](http://www.fliquidstudios.com/2009/03/19/installing-fedora-10-on-windows-xp-using-virtualbox/)

little more detail:

[http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15](http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15)

---

### Post by haqking on 2011-09-08
> **avi k said:**
> [SIZE=3]Thank you.

 I will look for a guide how to install Fedora on [/SIZE][SIZE=3]the[/SIZE] [SIZE=3]virtualbox.I hope there is a guide.

 Thank you.
[/SIZE][SIZE=3]
[/SIZE]


modify to suit [http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15](http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15)

---

### Post by avi k on 2011-09-09
Well I've got a problem here, after I run the virtual machine window popped, and it says that gnome can not work because of a problem, I am enclosing a picture:

[IMG]http://www.fastup.co.il/images/6475380.png[/IMG]My computer installed Windows operating system on drive it size is 1TB, the drive is separated into two drives Are called C and E ,in  Drive E  I installed the virtual system, the size of the drive is about 490 Gbit, can I fix the problem, and how I do it?.

---

### Post by NightwishFan on 2011-09-09
As far as I know, no. Try installing the virtualbox guest additions but I do not believe Gnome Shell works in virtualbox yet. Fallback mode, which you are using now should work fine.
[http://www.virtualbox.org/manual/ch04.html#guestadditions](http://www.virtualbox.org/manual/ch04.html#guestadditions)

---

### Post by haqking on 2011-09-09
> **NightwishFan said:**
> As far as I know, no. Try installing the virtualbox guest additions but I do not believe Gnome Shell works in virtualbox yet. Fallback mode, which you are using now should work fine.
[http://www.virtualbox.org/manual/ch04.html#guestadditions](http://www.virtualbox.org/manual/ch04.html#guestadditions)


yeah additions should fix it, though as you say Gnome shell may not be supported yet.

I know Unity works fine in a VM but you may have to wait for Gnome Shell support.
cheers

---

### Post by avi k on 2011-09-09
Thank you.
 I did not understand, what do you mean "Try installing the virtualbox guest additions", how I do it?, I have no experience in Linux.
 If you say it's still not working,which  system I can install?.

---

### Post by NightwishFan on 2011-09-09
No, it is fine in fallback mode obviously it is working. The 3d mode is not supported in virtualbox. (Neither is Windows 7 3d effects so its not a Linux thing)

Kind of in the wrong site asking for Windows help with Fedora in virtualbox. If anything you should be asking somewhere that helps with virtualbox.

---

### Post by haqking on 2011-09-09
> **NightwishFan said:**
> As far as I know, no. Try installing the virtualbox guest additions but I do not believe Gnome Shell works in virtualbox yet. Fallback mode, which you are using now should work fine.
[http://www.virtualbox.org/manual/ch04.html#guestadditions](http://www.virtualbox.org/manual/ch04.html#guestadditions)

> **avi k said:**
> Thank you.
 I did not understand, what do you mean "Try installing the virtualbox guest additions", how I do it?, I have no experience in Linux.
 If you say it's still not working,which  system I can install?.


read the link given to you from Nightwishfan above ;-)

---

### Post by avi k on 2011-09-09
Thank you.
 But the guide you gave me is not the same as what happens on my virtual system, it says, and I quote:

> Select "Mount CD/DVD-ROM" from the "Devices" menu in the             virtual machine's menu bar and then "CD/DVD-ROM image". This             brings up the Virtual Media Manager described in [the section called “The Virtual Media Manager”]("http://www.virtualbox.org/manual/ch05.html#vdis").

At the link given there is not the same as what happens in my system, here's a picture of what happens in the virtual system :So what to do now?.


[IMG]http://www.fastup.co.il/images/35693548.png[/IMG]

---

### Post by haqking on 2011-09-09
> **avi k said:**
> Thank you.
 But the guide you gave me is not the same as what happens on my virtual system, it says, and I quote:



At the link given there is not the same as what happens in my system, here's a picture of what happens in the virtual system :So what to do now?.


[IMG]http://www.fastup.co.il/images/35693548.png[/IMG]

From the guide and link you posted :

**Installation**

In the "Devices" menu in the virtual machine's menu bar,         VirtualBox has a handy menu item named "Install guest additions",         which mounts the Guest Additions ISO file inside your virtual machine.         A Windows guest should then automatically start the Guest Additions         installer, which installs the Guest Additions into your Windows         guest.
**Note**

For the basic Direct3D acceleration to work in a Windows Guest, you           have to install the Guest Additions in "Safe Mode".           This does **not** apply to the experimental           WDDM Direct3D video driver available           for Vista and Windows 7 guests, see [Chapter 14, *Known limitations*]("http://www.virtualbox.org/manual/ch14.html") for           details.[18]

If you prefer to mount the additions manually, you can perform         the following steps:

[LIST=1]
[*]Start the virtual machine in which you have installed             Windows.
[*]Select "Mount CD/DVD-ROM" from the "Devices" menu in the             virtual machine's menu bar and then "CD/DVD-ROM image". This             brings up the Virtual Media Manager described in [the section called &#8220;The Virtual Media Manager&#8221;]("http://www.virtualbox.org/manual/ch05.html#vdis").
[*]In the Virtual Media Manager, press the "Add" button and             browse your host file system for the             VBoxGuestAdditions.iso             file:
[LIST]
[*]On a Windows host, you can find this file in the                   VirtualBox installation directory (usually under                   C:\Program                   files\Oracle\VirtualBox ).
[*]On Mac OS X hosts, you can find this file in the                   application bundle of VirtualBox. (Right click on the                   VirtualBox icon in Finder and choose *Show Package                   Contents*. There it is located in the                   Contents/MacOS                   folder.)
[*]On a Linux host, you can find this file in the                   additions folder under                   where you installed VirtualBox (normally                   /opt/VirtualBox/).
[*]On Solaris hosts, you can find this file in the                   additions folder under                   where you installed VirtualBox (normally                   /opt/VirtualBox).
[/LIST]
 
[*]Back in the Virtual Media Manager, select that ISO file and             press the "Select" button. This will mount the ISO file and             present it to your Windows guest as a CD-ROM.
[/LIST]

Unless you have the Autostart feature disabled in your Windows         guest, Windows will now autostart the VirtualBox Guest Additions         installation program from the Additions ISO. If the Autostart feature         has been turned off, choose         VBoxWindowsAdditions.exe from the         CD/DVD drive inside the guest to start the installer.
The installer will add several device drivers to the Windows         driver database and then invoke the hardware detection wizard.
Depending on your configuration, it might display warnings that         the drivers are not digitally signed. You must confirm these in order         to continue the installation and properly install the         Additions.
After installation, reboot your guest operating system to         activate the Additions.

--------------------------------------------

From the devices menu choose to mount the vboxadditions.iso or unmount your current mounted .iso from the install

As mentioned your request is for fedora (not ubuntu) installed in virtual box in windows (not ubuntu)

---

