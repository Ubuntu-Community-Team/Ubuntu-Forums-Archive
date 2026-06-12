---
title: "Not A Neotype but new to Linux - need direction"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by linuxman1 on 2007-04-21
Was fairly impressed with Ubuntu 6.10 and even more so with 7.4 .  While the main hardware was recognized without difficulty, some of the other devices need to be setup and I am having some difficulty trying to navigate the necessary processes.  Before I ask specific questions let me describe the system hardware:

**User built system**:
P4 Case (with original PSU removed 
3 system fans + dedicated harddrive and DVD fans.
Antec TruePower 2.0 480W PSU
AMD Athlon64 x2 (AM2) 3500+ (retail ... fan and heatsink)
Gigabyte GA-M55Plus-S3G Motherboard (retail ... onboard Geforce 6100 and Realtec HD Audio)
Geil Ultra DDR2 PC6400 (Dual Channel) ... 2 x 512MB
Hitachi PATA 7200rpm 160GB Hard Drive
Pioneer DVD-WR (x16)
Floppy Drive
Logitech MX-Laser Mouse
Modware PS/2 Keyboard
Magview 17" CRT
Brother HL-2040 LaserJet
Epson Perfection 1260 Flatbed Scanner
Cambridge 5 piece Audio Speaker Set
Brother MFC-5440CN (connected over DSL Broadband)
LAN Home network via 2Wire DSL Modem Router.

No problems with the basic install but Scanner and Printers not initialized.  Through System->Administration->Printing, I was able to initialize the Brother HL-2040 Laserjet by selecting the HL-2060 driver from the dropdown list (as was suggested in a forum reference I had come across).

I know that Brother is actively developing Linux drivers for many of its hardware devices.  So my first set of questions are:
**Q#1**:  Brother has the devices listed under several categories and sub categories so which ones are applicable to Ubuntu?
CUPS vs CUPSWrapper
**Q#2**: It seems that the CUPSWrapper is the appropriate choice.  Is this correct?

**Q#3**: What type of CUPS Wrapper should be selected? Debian (DPKG) or SUSE, etc. (RPM)

According to Brother's website you first need to download and install LPD (LPR) before you can install the CUPS Wrapper driver.  
**Q#4**: Is this still the case with Ubuntu 7.4?

The install instructions require that you logion at the command prompt as root (or issue the SU command).  As a security enhancement Ubuntu requires that you login with a separate userid and password (has admin privileges).  
**Q#5**: From the desktop, what do I need to do to login as root (or issue the SU command with proper validation? 

The Brother MFC-5440 Inkjet/fax/scanner is deteced as a node on the LAN.
**Q#6**: Would I accept the "Detected" type or do I select the "Network" type if using the printing install utility?

Assuming that I can find an appropriate driver for the Epson Scanner, 
**Q#7**: What Option under the System Menu would I use to install the scanner?  Is there also a command string that must be executed to initialize the scanner or is the whole process handled through a GUI?

The above are of primary concern but I do have one more question.  The system seems a bit slow.  
**Q#8**: Are there some system tweaks that can be applied to improve performanace (such as having the OS recognize that DDR2 800Mhz memory is in use).

**Q#9:** Is it possible to modify the default wording of entries in the Boot Menu Screen?  I believe Ubuntu is using GRUB.  Is the file being stored on hd0 (first primary partition)?

I realize that some of these may ***not*** be considered "New User" type questions so if appropriate please direct me to a more suitable forum.

---

### Post by seshomaru samma on 2007-04-21
Don't think I can help you much , but here goes:
> Q#3: What type of CUPS Wrapper should be selected? Debian (DPKG) or SUSE, etc. (RPM)
you need Debian , Ubuntu is Debian based
> Q#5: From the desktop, what do I need to do to login as root (or issue the SU command with proper validation? 
'su' switches user to adminstrator, which is disabled by default in Ubuntu, you can create one , but actually there is no need. Instead you just use the 'sudo' in front of the command.
Let's say the website suggest you run this command:
```
dpkg -i brother_driver_or_something.deb
```
then to run as adminstaror/super user you just go:
```
sudo dpkg -i brother_driver_or_something.deb
```
> Q#9: Is it possible to modify the default wording of entries in the Boot Menu Screen? I believe Ubuntu is using GRUB. Is the file being stored on hd0 (first primary partition)?
yes
first make a backup of the grub menu:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```
then edit it like this:
```
sudo gedit  /boot/grub/menu.lst
```
if you want to change the wording you need to change this line:
```
title		[COLOR="Red"]Ubuntu, kernel 2.6.15-28-386[/COLOR]
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot
```
to whatever you want

---

### Post by harun on 2007-04-21
I have a brother HL-2040. Didn't do a thing, Ubuntu recognized it and I was off and printing.

---

### Post by linuxman1 on 2007-04-21
Thanks for the help.  Under Ubuntu 6.1, the Brother HL-2040 didn't seem to be recognized but that may be because I was trying to get used to the OS (I can't recall if there was a Printing Option under the System/Administration Menu).  I am also using the parallel connection instead of the USB (for some reason this stopped working in Windows 2000).  The bigger challenge is getting the other two devices to work.

---

### Post by seshomaru samma on 2007-04-21
> The above are of primary concern but I do have one more question. The system seems a bit slow.
Q#8: Are there some system tweaks that can be applied to improve performanace (such as having the OS recognize that DDR2 800Mhz memory is in use).

I don't know how to make Ubuntu recognise DDR2 (perhaps it does)
but the main factor that determains the speed seems to be the kind of graphic interface one is using.
By default , Ubuntu comes with Gnome as its graphic environment, Gnome is very user friendly but takes a lot of resources. If you install a lighter environment such as Fluxbox or Icewm , your computer will run MUCH faster
To install icewm run this command:
```
sudo aptitude install icewm
```
log out and choose 'icewm' in the sessions option on the login screen
(same procedure for fluxbox)
these light environments take a while to get used to. They use a lot of keybinding and are highly flexible. more info in [this thread]("http://ubuntuforums.org/showthread.php?t=263710") , some IceWM tips[ here ]("http://forums.debian.net/viewtopic.php?t=5450") and Fluxbox tips [here]("http://forums.debian.net/viewtopic.php?t=5382") (notice that these tips are for Debian , you might need to make some little adjustments for Ubuntu) , my own tip is if you want to have desktop icons in IceWM - install idesk.
XFCE is somewhere between Gnome and Icewm , you can try it ,it's somewhat friendlier than IceWM but not as fast.

You can ,however, speed up the system ,even in Gnome - here are some tips: [http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

---

