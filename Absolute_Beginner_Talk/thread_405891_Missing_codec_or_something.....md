---
title: "Missing codec or something...."
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by ginnie6 on 2007-04-10
I can't view utube or any online video clips anymore. Without me spending hours looking can someone tell me what I need so I can see these again? Right now all I can see is a big black box with red buttons in the middle.

---

### Post by Grayman on 2007-04-10
Try these steps to install mplayer. Worked for me.

from terminal, type:

sudo aptitude install mozilla-mplayer

When that's finished, get the codecs type typing:

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
```

Install the codecs:

sudo dpkg -i w32codecs_20061022-0.0_i386.deb

Then, with Firefox closed, remove the totem plugins:

sudo rm /usr/lib/firefox/plugins/libtot*

Good luck!

Gray

---

### Post by rufius on 2007-04-10
You probably need the flash plugin. ```
apt-get install flashplugin-nonfree
```

---

### Post by ginnie6 on 2007-04-10
I'm using opera not firefox. after installing it says nothing to be installed updated or removed. With the second command I get an error message say8ing no such file or command. I haven't even tried firefox to see if they're viewable there.....they are so its just a problem with my opera. any other ideas?

---

### Post by rufius on 2007-04-10
What does this command return? ```
apt-cache search flash
```

---

### Post by ginnie6 on 2007-04-10
ginnie6@ginnie6-desktop:~$ apt-cache search flash
keduca - interactive form-based tests for KDE
kipi-plugins - image manipulation/handling plugins for KIPI aware programs
kvoctrain - vocabulary trainer for KDE
kwordquiz - flashcard and vocabulary learning program for KDE
flashplayer-mozilla - Macromedia Flash Player
microcode.ctl - Intel IA32/IA64 CPU Microcode Utility
konqueror - KDE's advanced file manager, web browser and document viewer
gnash - free Flash movie player
gnash-tools - free Flash movie player - Command-line Tools
klash - free Flash movie player
konqueror-plugin-gnash - free Flash movie player - Plugin for Konqueror
libgnash0 - free Flash movie player - shared libraries
mozilla-plugin-gnash - free Flash movie player - Plugin for Mozilla and derivatives
flashplugin-nonfree - Adobe Flash Player plugin installer
adzapper - proxy advertisement zapper add-on
aget - Multithreaded HTTP Download Accelerator
avrp - Programmer for Atmel AVR microcontrollers
childsplay-lfc-names-fr - French files for the Letter Flash Cards game
childsplay-lfc-names-nl - Dutch files for the Letter Flash Cards game
childsplay-plugins-lfc - letterFlashscard game for childsplay
flashybrid - automates use of a flash disk as the root filesystem
flasm - assembler and disassembler for Flash (SWF) bytecode
ftdi-eeprom - Tool for reading/erasing/flashing FTDI USB chip eeproms
fujiplay - Interface for Fuji digital cameras
granule - flashcard program for learning new words
gstreamer0.8-swfdec - SWF (Macromedia Flash) decoder plugin for GStreamer
ifpgui - QT based manager for iRiver iFP audio players
libflash-dev - GPL Flash (SWF) Library - development files
libflash-mozplugin - GPL Flash (SWF) Library - Mozilla-compatible plugin
libflash-swfplayer - GPL Flash (SWF) Library - stand-alone player
libflash0c2 - GPL Flash (SWF) Library - shared library
libimage-size-perl - determine the size of images in several common formats
libming-dev - Library to generate SWF (Flash) Files (development files)
libming-util - Library to generate SWF (Flash) Files - Utilities
libming0 - Library to generate SWF (Flash) Files
liborange-dev - development libraries for liborange
liborange0 - library to extracts CAB files from self-extracting installers
libroxen-flash2 - Flash2 module for the Roxen Challenger web server
libswf-perl - Ming (SWF) module for Perl
libswfdec0.3 - SWF (Macromedia Flash) decoder library
libswfdec0.3-dev - SWF (Macromedia Flash) decoder library
libtk-tablematrix-perl - Table/matrix widget extension to Perl/Tk
m16c-flash - Flash programmer for Renesas M16C and R8C microcontrollers
mathwar - A flash card game designed to teach maths
memaid-pyqt - memorization tool with optimal question scheduling
ming-fonts-dejavu - Ming format DejaVue Fonts
ming-fonts-opensymbol - Ming format Opensymbol Fonts
mtasc - ActionScript 2 to Flash (SWF) compiler
mtd-tools - memory Technology Device Tools
newsflash - gets news with the newnews command from a server
openwince-jtag - allows programming jtag capable devices such as CPUs or FPGAs
orange - extracts CAB files from self-extracting installers
php-image-graph - Image_Graph module for PEAR
ploticus - script driven business graphics package
python-ming - Ming (SWF) module for Python
redboot - Red Hat Embedded Debug and Bootstrap firmware
swf-player - Mozilla plugin for SWF files (Macromedia Flash)
texlive-latex-extra - TeX Live: LaTeX supplementary packages
upslug2 - utility to upgrade the firmware of a LinkSys NSLU2 via the network
vrflash - tool to flash kernels and romdisks to Agenda VR
weechat - Fast, light and extensible IRC client
weechat-curses - Fast, light and extensible IRC client
weechat-scripts - script collection for the WeeChat IRC client
xbox-cromwell - Xbox BIOS image
xbox-raincoat - Xbox BIOS flasher
xchat-systray - xchat systray notification icon
xmms-jess - visualization plugin for XMMS using various 2D and 3D method

---

### Post by Maestro23 on 2007-04-10
In terminal:

> sudo aptitude install flashplugin-nonfree


---

### Post by ginnie6 on 2007-04-10
ginnie6@ginnie6-desktop:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by rufius on 2007-04-10
> **Maestro23 said:**
> In terminal:

correction: ```
sudo apt-get install flashplugin-nonfree
``` 

OR

```
sudo aptitude install flashplugin-nonfree
```

---

### Post by Maestro23 on 2007-04-10
Thanks Rufios, one too many "t's" in there.:) 

To the OP, you need to enable all your repositories if you are not seeing the plugin.

Adding Extra Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

After that, try the install again.

---

### Post by ginnie6 on 2007-04-10
I have all the repositories enabled and it says 


ginnie6@ginnie6-desktop:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ginnie6@ginnie6-desktop:~$ 

it has to be something really stupid I'm missing.....

---

### Post by Maestro23 on 2007-04-10
Nevermind, it says you already have the plugin installed.   Do you have all your codecs installed?  Check the Restricted Formats link: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by arnego2 on 2007-12-31
Hello there 
I had a similar problem with konqueror which I solved that way:
sudo aptitude install konqueror-nsplugins 
regards 
Arnego2

---

