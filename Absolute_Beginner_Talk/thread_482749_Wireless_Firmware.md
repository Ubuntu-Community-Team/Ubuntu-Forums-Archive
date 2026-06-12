---
title: "Wireless Firmware?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by FlyinRedneck on 2007-06-24
Where can i find the firmware athfmwdl (Atheos USB, or something like that)? Can i find it under my windows OS? Or must i dowload it?

I have a Netgear WPN111 USB 2.0 adapter and i am trying to get it to work. I want to make sure i have everything i need before i swich my OS over to ubuntu.

I have:

NDISwrapper ( but i only have a very vague idea of how to install it and use it)
WPN111.sys (driver file)
netwpn11.inf ( I think i know where this is on windows)

any help will be appreciated.

---

### Post by kevdog on 2007-06-24
Not trying to blow you off, but why dont you read the installation instructions from the ndiswrapper website.  I will tell you how to check your card to see if its even compatible with ndiswrapper.  If it is, it will suggest a driver (possibly different than what you have), and it has a very good documentation on how to install the package.  The only prerequisite that the documentation doesnt have is that you have to install the build-essential package first.  If you have an ethernet connection (ie a wired connection) then type at command line:
sudo aptitude install build-essential

If you do not, you will need the install Ubuntu Cd. Place in drive, then type
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

Then proceed with the instructions as per the website.  You may need another computer to download the actual ndiswrapper source files and then transfer to the ubuntu machine via USB stick

Good luck:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by FlyinRedneck on 2007-06-24
I have read that. It does support my hardware. But, i cant find one of the drivers i need. (the one i originally posted) I just would like to know where to find it. The site fails to tell where.

---

### Post by kevdog on 2007-06-24
Did you consult the list section on the website?? Its under documents/wiki->List.  If you need more help please for me cut and paste what is suggests under the list section.  Thanks.

---

### Post by FlyinRedneck on 2007-06-24
yes i did. here is what it suggests.

Card: Netgear WPN111 108Mbps RangeMAX USB (with super G/MIMO)
Chipset: Atheros USB
pciid: 1358:5f01 
Driver: Windows XP driver available on the Netgear CD: netwpn11.inf + wpn111.sys + ar5523.bin
Other: Install both wpn11 and [COLOR="Red"]athfmwdl [/COLOR]drivers.


the one in red is the driver i am talking about.

---

### Post by kevdog on 2007-06-24
Ive never installed this driver before, but here is what I found from another post [http://ubuntuforums.org/showthread.php?t=258732](http://ubuntuforums.org/showthread.php?t=258732).  Basically the file should be located somewhere on your wireless CD named athfmwdl.inf.

> I found out today that on the driver cd there is another .inf file that is called athfmwdl.inf. Install that through ndisgtk and it'll work on bootup. This is the bootloader driver.

Just a small variation from the normal documentation, sounds to me like you have to do the following (make sure all files in same directory):
sudo ndiswrapper -i athfmwdl.inf
sudo ndiswrapper -i netwpn11.inf

Check installation with 
ndiswrapper -l

If everything looks good:
sudo modprobe ndiswrapper

Let me know what you find.

---

### Post by FlyinRedneck on 2007-06-24
There is one slight problem. All the driver files are not in a cd but they are in a windows executable file. Is there a way to pluck the file out?

---

### Post by kevdog on 2007-06-24
The exe file may represent a self-extracting zip file, or a cabinet file.  It could be either.  If a zip file I think you can simply open file with ark or another of ubuntu's tar.gz programs (seem to remember a command unzip somewhere??).  If its a cabinet file you need to install the package cabextract.  I dont remember the exact syntax of this command but its something like cabextract *****.exe <---Substitute cabinet file name.

---

### Post by ghost_ryder35 on 2007-06-24
if the driver is installed you should be able to copy and paste them into a folder on a thumb drive and move them to the linux install.  and or download the driver from the vendors website and extract them into a folder

---

### Post by FlyinRedneck on 2007-06-24
ok i have tried to extract the cab files like a thousand times. it wont work.

---

### Post by FlyinRedneck on 2007-06-24
after a few hours of deliberation, I cannot find the athfmwdl driver anywhere.

on top of that i am having some weird errors with ndiswrapper. i think it may have to go with the fact that ther is no .config files in the destination folders. I think i can find te answe to this on the forums.

But............ Does anyone know where to get the Athfmwdl driver? it isnt in my computer. it isnt in my window's istalation CD .cab files. no where.

HELP!!!!!!!!!!!!

---

### Post by kevdog on 2007-06-24
Google is your friend -- relax.  If you have installed this device on windows, it has to be somewhere.

---

