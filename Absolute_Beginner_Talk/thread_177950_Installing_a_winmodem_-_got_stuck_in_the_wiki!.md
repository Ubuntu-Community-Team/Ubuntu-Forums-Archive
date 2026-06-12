---
title: "Installing a winmodem - got stuck in the wiki!"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by davidathome on 2006-05-17
Hello all,

I've just installed Breezy and have it problems with my winmodem [I only have dial up and have no desire to go out and try and find hard modems].  I've followed the wiki and have got to the point where I have downloaded the files and the right driver [Intel 386 driver] and these sit on a usb stick.

When I try and follow the install using dpkg as shown in the wiki I get an error message saying the files cannot be found.:confused: 

Its probably something very simple but I just don't know how to get the files installed from the usb stick!

Please help!

Thanks, and apologies if I've posted in the wrong place but I couldn't find any answers on a search of the forums.

David

---

### Post by Sef on 2006-05-17
What is your make and model of your winmodem?

---

### Post by davidathome on 2006-05-17
Its an Intel 536 EP.

I've got the required files from the instal disc for Breezy and the package files listed in the wiki as being available from archive.ubuntu as well as the driver from intel.  I can't figure out how to get them from the usb stick though as the command sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb is saying that it can't find it - I assume I need to tell it to look on the usb stick somehow?

---

### Post by gr0kzer0 on 2006-05-17
Your usb stick should have a filename which ubuntu knows it by.

For example, ubuntu calls my floppydrive /media/floppy0.  Let's say that on my floppy disk is a file called "file".

If I want to delete that file, I have to type

rm /media/floppy0/file

What's your usb stick known as to ubuntu?

---

### Post by davidathome on 2006-05-17
[QUOTE=gr0kzer0]

What's your usb stick known as to ubuntu?[/QUOTE]

It shows up as media/usbdisk and contains a foldr/linux and within the folder are the various files, 4 in total to include the driver file.

David

---

### Post by davidathome on 2006-05-19
So, having identified *where* the files are, where do I put the path in the following command please?

sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb

---

### Post by dmizer on 2006-05-19
well, just copy the files from your stick to the home directory with nautilus (or kommander if you have kde), and then run the dpkg command.

---

### Post by joshrobinson on 2006-05-19
[QUOTE=dmizer]well, just copy the files from your stick to the home directory with nautilus (or kommander if you have kde), and then run the dpkg command.[/QUOTE]

that will work or you can do this in a terminal

cd /media/usbdisk/linux

then your sudo dpkg command

---

### Post by gr0kzer0 on 2006-05-19
What I'd do is something like this.  Move the package to your Desktop

```
mv /media/usbdisk/package.deb ~/Desktop/package.deb
```

Then navigate to the Desktop yourself

```
cd ~/Desktop
```

Then give the command to install the package

```
sudo dpkg -i package.deb
```

Of course, edit these commands to fit your particular circumstances.  I hope it works out for you.  I "successfully" installed the driver for my winmodem, but it still didn't work.  I'm waiting to get Dapper, then I'll try again.

---

### Post by davidathome on 2006-05-19
Thanks to all for the replies and your patience I'm aware that the question is very basic but I hope to improve over time!

---

### Post by davidathome on 2006-05-20
Well, I gues ubuntu is not for me.

I tried all the suggestions but it still can't find the file to install it.

Trying cd to both the usbstick and desktop brought up error messages that the directory couldn't be found.

Copying the file to desktop and running the command said the file couldn't be found despite it sitting there on the desktop in clear view and having 'properties' against it when looking at it through the file browser.

So, I've concluded that as I can't get it to work I'll have to try and find a distro that will find my winmodem for me as I'm fed up of booting betwen windoxe and linux.  Damn!

---

### Post by dmizer on 2006-05-21
if you copied the file to your desktop, you have to make sure that you change your command line to the desktop directory before it will see the file.

that is ... when you open a terminal, you see something like this:
```
dmizer@injapan:~$
```
notice the little ~ ... that means your current directory when you oppen the command line is your home directory (in my case) /home/dmizer

to get to your desktop so you can install your file, you just need to change to the desktop directore like so:
```
cd Desktop/
```
**make sure that when you type desktop that it has an upper case 'd'** ... linux is case sensitive.

once you are in the correct directory, then you will be able to do your install.

something to take note of here is that what you are experiencing in the command line is no different in linux than it is in windows.  if you open a commandline and try to run a program you have saved on your windows desktop, you will be unable to do so.  you will have to change your directory in windows as well.

give it one more shot, and if you still can't get it to install, then i suggest serious research before switching to a different distro.  dial up win modems are probably one of the more difficult things to get working correctly in linux.

---

### Post by Matchless on 2006-05-21
Hi,
     I can promise you Intel536EP does work. Here is a slightly simplified version from the Wiki.

Modems supported by the Intel536EP driver for Ubuntu Dapper
This page describes how to install the driver for the Intel 536EP internal modem on Ubuntu Dapper for i386 systems. Some of these are sold as Cnet modems and have Ambient chips on board. The process below is quick easy and works quite well. For other older ubuntu versions you will additionally require gcc 3.4 to also to be installed. 
Install required Ubuntu packages
In a terminal type $uname-r, which should give you something like VERSION-XX-ARCH (where ARCH is your kernel flavor, e.g. 386, 686, 686-smp, k7 or k7-smp if you use Intel, powerpc for PPC ...). 
Ubuntu Dapper Drake 6.06 
You will need to install the build-essential and linux-headers-ARCH packages. They are normally on the install CD and can most easily be installed with Synaptic. If you need to download these due to later versions connect to another PC via the network card and download and install with Synaptic.
Download the drivers for the modem here: 
 [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng) 
Save the file, which is named Intel-536EP-4.71.tgz; on your Desktop. 
Compiling the driver
Right click on the file and select “Extract to here” This will create directory Intel-536 with the source on your Desktop. Open a terminal window and type: 
 cd Desktop/Intel-536
Type: 
 make clean
This should produce output looking like this: 
 Try `uname --help' for more information.
 cd coredrv; make clean
 make[1]: Entering directory `/home/rory/Intel-536/coredrv'
 rm -f *.ko *.o *~ core
 make[1]: Leaving directory `/home/rory/Intel-536/coredrv'
 rm -f *.o *.ko
Now type 
 make 536
This will result in many lines of output being printed to the terminal window; you can ignore most of them. The final lines should look like this: 
   CC      /home/<username>/Intel-536/coredrv/Intel536.mod.o
   LD [M]  /home/<username>/Intel-536/coredrv/Intel536.ko
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
 make[1]: Leaving directory `/home/<username>/Intel-536/coredrv'
There should be an Intel536.ko file in the directory now; test this by typing
 ls -l Intel536.ko 
The output should look like:
 -rw-r--r--  1 <username><username> 1070980 2006-05-06 21:02 Intel536.ko
Your dates and times will be different. If you are using Dapper, the file size (1070980) should be the same. 
Installing the driver
There are two steps to installing the driver. The first is to copy the Intel536.ko file created above to an appropriate directory, and the second is to cause the driver to be loaded at boot time. 
To install the Intel536.ko file, copy the file to the modules directory with this command: 
 sudo cp Intel536.ko /lib/modules/$(uname -r)/kernel/drivers/char
Make your system aware of this module with depmod: 
 sudo depmod -a
Finally, load the driver with the modprobe command: 
 sudo modprobe Intel536
This command should not print a response; if it prints something like this: 
 FATAL: Module Intel536 not found.
you have made an error; most likely you have copied the file to the wrong place. If you see a different error message, there may be an error in the module, or your modem, or you may not have a Intel 536-based modem. 
Loading the driver at boot time 
To load the module at boot time, we need to add a line "Intel536" to the file /etc/modules.
Open the file /etc/modules and with kwrite, Kate or Gedit and enter a line at the end:
Intel536
Using the modem
The name of your modem device is /dev/536ep0. You can now use sudo pppconfig to set up pon & poff. To use Kppp you will need to create a symlink be able to link the /dev/536ep0 to /dev/modem. Udev rewrites the /dev on each reboot and you thus have to create a new file with kwrite, kate or gedit in /etc/udev/rules.d/10-local.rules and put the following lines in it: 
 	# Intelmodem536ep
 KERNEL="536ep0", SYMLINK="modem"
Now reboot and you can use Kppp to query the modem as this is a quick check if all is well before dialling out. Configure KPP for your ISP connection. These Intel modems are found to be more stable and less finicky that the Smartlink types on Ubuntu.

---

