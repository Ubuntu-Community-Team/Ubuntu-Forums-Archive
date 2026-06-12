---
title: "[SOLVED] How do I install a windowsXP in a VirtualBox?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-20
HOw do I install a windowsXP in a VirtualBox?

=============
00:00:04.231 VirtualBox 1.5.0_OSE r4471 (Oct 15 2007 14:45:13) release log
00:00:04.231 Log opened 2007-12-20T10:43:37.591547000Z
00:00:04.231 ERROR [COM]: aRC=0x80004005 aIID={1dea5c4b-0753-4193-b909-22330f64ec45} aComponent={Console} aText={The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
00:00:04.231 VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE)} aPreserve=false
00:00:04.250 Power up failed (vrc=VERR_VM_DRIVER_NOT_ACCESSIBLE, hrc=0x80004005)

---

### Post by MozartlovesUbun2 on 2007-12-20
overdrank  overdrank is offline
Feliz Navidad
	  	
Join Date: Feb 2007
Location: 30.46N -87.19W Elev. 92
Bean Count Hidden
Ubuntu 7.10 Gutsy Gibbon User
Send a message via Yahoo to overdrank
Re: VirtualBox problem.
Quote:
Originally Posted by eXeCuTeR+ View Post
Anytime I try to start Windows I get this message:
Code:
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
Result Code: 
0x80004005
Component: Console
Interface: Console {1dea5c4b-0753-4193-b909-22330f64ec45}

How do I fix this?

Thanks.
Hi if you use this command in the terminal
Code:

**sudo chmod 666 /dev/vboxdrv**

that should solve that issue. And if you will check out the user manual it has great info
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Good luck!

---

### Post by insane_alien on 2007-12-20
or do it the proper way and go to 'users and groups' click manage groups and edit the vboxdrv group and add yourself to it.

---

### Post by hyper_ch on 2007-12-20
wouldn't the proper way be through the terminal? ;)

---

### Post by MozartlovesUbun2 on 2007-12-20
**sudo chmod 666 /dev/vboxdrv** did the trick  (why can't this be done by default when one install the VirtualBox?)

now do i need to install TOOLS inside the virtual machine, or anything else?

(like VMWare has** "VMWare Tools" ** which is later installed inside the virtual machine)

all tips are welcome, thanks

---

### Post by hyper_ch on 2007-12-20
just because it did the trick doesn't mean, that it's good to do it. I tend to think there is a reason why that folder didn't have those permissions. Think about it ;)

---

### Post by rechick on 2007-12-20
If you would like auto mouse capture/release as well as cut and paste, install the tools. If the OSE version is installed the tools will be automatically downloaded once you agree to the terms. If this is for personal use then go ahead. If this is for business use you are supposed to purchage the program from the company.

---

### Post by GSF1200S on 2007-12-20
Do as was mentioned above and go to System>Administration>Users and Groups and edit the vboxdrv to inlude you as a user. When you reboot the "chmod666" command wont be in effect and youll have to keep re-entering it. You dont want to use that command unless necessary.

---

### Post by MozartlovesUbun2 on 2007-12-20
> **hyper_ch said:**
> just because it did the trick doesn't mean, that it's good to do it. I tend to think there is a reason why that folder didn't have those permissions. Think about it ;)

sorry i am confused here

what does this mean?

can someone help?

also how can i be sure if the tools are installed, this is just for personal use not corporate.

================================

**ok i did, now how do i remove the (sudo chmod 666 /dev/vboxdrv) if it's not good???**

system>administration>users and groups>manage groups

select vboxusers > properties

check your own name.

---

### Post by GSF1200S on 2007-12-20
> **MozartlovesUbun2 said:**
> sorry i am confused here

what does this mean?

can someone help?

also how can i be sure if the tools are installed, this is just for personal use not corporate.

That command gives vboxdrv (the virtualbox kernel driver) authorization for any user to use it, at least as I understand it. This is considered undesirable generally...

Where it effects you is where you have to input the command every time you restart the computer. If you add your username to the vboxdrv in Users & Groups, you wont have to do this every restart, and the desired priveledges will be satisfied. ;)

---

### Post by Taboo Mirage on 2007-12-20
You don't even have to restart the computer; just logout and log back in again.

---

### Post by MozartlovesUbun2 on 2007-12-20
> **GSF1200S said:**
> That command gives vboxdrv (the virtualbox kernel driver) authorization for any user to use it, at least as I understand it. This is considered undesirable generally...

Where it effects you is where you have to input the command every time you restart the computer. If you add your username to the vboxdrv in Users & Groups, you wont have to do this every restart, and the desired priveledges will be satisfied. ;)

ok thanks

now i am having troubles with the shared folders

i installed VirtualBox as i thought that they said it works

but apparently not in the free version? only in the paid version?

how do i solve this, and are there any other tweaks or tools to install, if so, how?

thanks

---

### Post by KCPokes on 2007-12-20
[http://virtualbox.org/download/UserManual.pdf](http://virtualbox.org/download/UserManual.pdf)

The manual walks through how to set up the Additions as well as how to set up shared folders.  A linux host with a Windows guest is pretty straightforward, but the shared folders might require a quick gander at the documentation.

---

### Post by MozartlovesUbun2 on 2007-12-21
shared folders looks horrible

so much to setup and install

i think i will move to VMWare

---

### Post by MozartlovesUbun2 on 2007-12-21
ok found it, here is the guest additions installer

**but i still havnt found out how to share folders**
==========================

                            4 The VirtualBox Guest Additions
4.2.1.1 Mounting the Additions ISO file
In the &#8220;Devices&#8221; menu in the virtual machine&#8217;s menu bar, VirtualBox has a handy menu
item named &#8220;Install guest additions&#8221;, which will automatically bring up the Additions
in your VM window.
   If you prefer to mount the additions manually, you can perform the following steps:
    1. Start the virtual machine where you have installed a Windows guest operating
       system.
    2. Select &#8220;Mount CD/DVD-ROM&#8221; from the &#8220;Devices&#8221; menu in the virtual machine&#8217;s
       menu bar and then &#8220;CD/DVD-ROM image&#8221;. This brings up the Virtual Disk Man-
       ager described in chapter 3.5, The Virtual Disk Manager, page 34.
    3. In the Virtual Disk Manager, press the &#8220;Add&#8221; button and browse your host file
       system for the VBoxGuestAdditions.iso file:
          &#8226; On a Windows host, you can find this file in the VirtualBox installation
            directory (usually under C:\Program files\innotek VirtualBox).
          &#8226; On a Linux host, you can find this file in the additions folder under where
            you installed VirtualBox (normally /opt/VirtualBox-1.5.2).
    4. Back in the Virtual Disk Manager, select that ISO file and press the &#8220;Select&#8221; but-
       ton. This will mount the ISO file and present it to your Windows guest as a
       CD-ROM.
4.2.1.2 Running the installer
Unless you have the Autostart feature disabled in your Windows guest, Windows will
now autostart the VirtualBox Guest Additions installation program from the Additions
ISO. If the Autostart feature has been turned off, choose setup.exe from the CD/DVD
drive inside the guest to start the installer.


                        .
**4.2.2 Updating the Windows Guest Additions**
Windows Guest Additions can be updated by running the installation program again,
as previously described. This will then replace the previous Additions drivers with
updated versions.
  Alternatively, you may also open the Windows Device Manager and select &#8220;Update
driver...&#8220; for two devices:
                                         
[B]   1. the VirtualBox Graphics Adapter and
   2. the VirtualBox System Device[/B].
  For each, choose to provide your own driver and use &#8220;Have Disk&#8221; to point the wizard
to the CD-ROM drive with the Guest Additions.

---

### Post by MozartlovesUbun2 on 2007-12-21
**YES, it fricking works!**

 There are two types of shares:
  1. VM shares which are only available to the VM for which they have been defined;
  2. transient VM shares, which can be added and removed at runtime and do not
     persist after a VM has stopped; for these, add the -transient option to the
     above command line.
 Then, you can mount the shared folder from inside a VM the same way as you would
mount an ordinary network share:
   • In a Windows guest, starting with VirtualBox 1.5.0, shared folders are
     browseable and are therefore visible in Windows Explorer. So, to attach the
     host’s shared folder to your Windows guest, open Windows Explorer and look
     for it under “My Networking Places” -> “Entire Network” -> “VirtualBox Shared
     Folders”. By right-clicking on a shared folder and selecting “Map network drive”
     from the menu that pops up, you can assign a drive letter to that shared folder.
     Alternatively, on the Windows command line, use the following:

---

