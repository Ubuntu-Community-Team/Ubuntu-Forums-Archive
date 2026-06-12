---
title: "Not A Neotype but new to Linux - need direction"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by linuxman1 on 2007-04-21
Was fairly impressed with Ubuntu 6.10 and even more so with 7.4 . While the main hardware was recognized without difficulty, some of the other devices need to be setup and I am having some difficulty trying to navigate the necessary processes. Before I ask specific questions let me describe the system hardware:

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

No problems with the basic install but Scanner and Printers not initialized. Through System->Administration->Printing, I was able to initialize the Brother HL-2040 Laserjet by selecting the HL-2060 driver from the dropdown list (as was suggested in a forum reference I had come across).

I know that Brother is actively developing Linux drivers for many of its hardware devices. So my first set of questions are:
**Q#1**: Brother has the devices listed under several categories and sub categories so which ones are applicable to Ubuntu?
CUPS vs CUPSWrapper
**Q#2**: It seems that the CUPSWrapper is the appropriate choice. Is this correct?

**Q#3**: What type of CUPS Wrapper should be selected? Debian (DPKG) or SUSE, etc. (RPM)

According to Brother's website you first need to download and install LPD (LPR) before you can install the CUPS Wrapper driver.
**Q#4**: Is this still the case with Ubuntu 7.4?

The install instructions require that you logion at the command prompt as root (or issue the SU command). As a security enhancement Ubuntu requires that you login with a separate userid and password (has admin privileges).
**Q#5**: From the desktop, what do I need to do to login as root (or issue the SU command with proper validation?

The Brother MFC-5440 Inkjet/fax/scanner is deteced as a node on the LAN.
**Q#6**: Would I accept the "Detected" type or do I select the "Network" type if using the printing install utility?

Assuming that I can find an appropriate driver for the Epson Scanner,
**Q#7**: What Option under the System Menu would I use to install the scanner? Is there also a command string that must be executed to initialize the scanner or is the whole process handled through a GUI?

The above are of primary concern but I do have one more question. The system seems a bit slow.
**Q#8**: Are there some system tweaks that can be applied to improve performance (such as recognizing that DDR2 800Mhz memory is in use).

**Q#9**: Is there a way to edit the default entries that appear on the bootloader screen?  I believe that Ubuntu is using GRUB and the file(s) is stured on the hd0 partition.

I realize that some of these may ***not*** be considered "New User" type questions so if appropriate please direct me to a suitable forum.

---

### Post by spin2cool on 2007-04-21
a few answers:

5) getting root priveleges is just a matter of typing 'sudo' in front of the command (and you'll be prompted for the password.  You'll need to append sudo to any command you wish to run as root.

9)  To edit the entries that GRUB displays, edit the file /boot/grub/menu.lst.  (you'll need to use your newfound sudo command to do so - "sudo gedit /boot/grub/menu.lst"

Be sure to make a backup of the menu file before you make any changes.

---

### Post by spin2cool on 2007-04-21
oh, and if you're having performance issues, you might want to try out the nvidia drivers - they're fairly easy to install with the help of Envy:  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Be sure to back up your /etc/X11/xorg.conf file before installing the drivers, so you can revert if necessary.

---

### Post by linuxman1 on 2007-04-21
Thanks, appreciate the quick response.:KS

---

### Post by AAM on 2007-04-21
> The install instructions require that you logion at the command prompt as root (or issue the SU command). As a security enhancement Ubuntu requires that you login with a separate userid and password (has admin privileges).
Q#5: From the desktop, what do I need to do to login as root (or issue the SU command with proper validation?
I may be misunderstanding you but the way to run **root** commands in Ubuntu is to preface them with **sudo**, e.g.,
> sudo gedit /etc/iftab
allows you to run the gedit program as **root** or superuser (no difference).

> Assuming that I can find an appropriate driver for the Epson Scanner,
Q#7: What Option under the System Menu would I use to install the scanner? Is there also a command string that must be executed to initialize the scanner or is the whole process handled through a GUI?
I think if you check with the **Xsane Image Scanner** (you will find this under **APPLICATIONS | GRAPHICS** in the Menu, the scanner will probably already be recognised. If not, good luck!

> Q#9: Is there a way to edit the default entries that appear on the bootloader screen? I believe that Ubuntu is using GRUB and the file(s) is stured on the hd0 partition.
You can edit GRUB manually, the relevant file is held at /boot/grub/menu.lst, but I would suggest that you do a bit of reading around first before hacking (as in destroying rather than coding!) your install. You should back up the menu.lst file before embarking on any grandiose scheme of machine domination. If you find your self GRUB-less, use the liveCD to boot and then resubstitute your old menu.lst file.

That's about all I c an help you with!

---

### Post by linuxman1 on 2007-04-21
Thanks for all the support.  As a community, you folks are amazing; and I have been involved in and around support for many, many years.  If this is a real reflection of the Ubuntu community, I expect fantastic thing to happen with this product.  I am actually getting excited!!!:KS :KS :KS :KS :KS 

I guess I may have to play around on my own to get answers to the Network Printer question.

---

### Post by spin2cool on 2007-04-21
Search around this forum - many many questions have been asked and answered here, and odds are someone has had a similar problem that's been resolved.

---

