---
title: "installing ATI driver"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Aximilli on 2006-05-14
I downloaded from ati.com their linux driver file, ati-driver-installer-8.24.8-x86.run, but when I try to run the file it attempts to open in gedit, which it cannot do. How do i run this file?

Thanx

---

### Post by aktiwers on 2006-05-14
Take a look at this guide.

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Remember to check if it is for your Card.

---

### Post by Aximilli on 2006-05-14
I'v looked at this before, but I tried again. I followed the directions for using ATI drivers, and got to the first code it asked me to put it. This is my code:

code
> 
 sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant



Where do i go from here?

---

### Post by catlett on 2006-05-14
When you double click on it does it give you the option to "run it in the terminal"?

---

### Post by Aximilli on 2006-05-14
I'v been following your advice in bman's thread. I have run ati's installer, but when i install the distro-specific driver i get an error message that points me to a log file, which doesn't tell me anything at all really.

---

### Post by xXx 0wn3d xXx on 2006-05-14
[QUOTE=Aximilli]I'v been following your advice in bman's thread. I have run ati's installer, but when i install the distro-specific driver i get an error message that points me to a log file, which doesn't tell me anything at all really.[/QUOTE]
Put the file on your desktop. Then right click the file and click the permissions tab. Make sure the owner is your username and check all the boxes. Now, open terminal and become root. 

> sudo su

Then move to your desktop:

> cd Desktop

And run the file:

> ./ati-installer-8.24.8-whatever
Remember to replace ati-installer-8.24.8-whatever with the name of the file.

Then it should run and install.

---

### Post by Aximilli on 2006-05-14
I know have an ATI control panel app. but when i go to start it i get the error message "Driver does not provide the FireGl X11  Extensions! Panel components will operate only partially." Then I have a useless one panel control box. I know I picked radeon and not firegl when i was at ati.com.  Ahh!

---

### Post by catlett on 2006-05-14
I though I'd see if it could be easy and double click it. Sometimes that will run the program from the terminal.
My first thought is do you have the right driver. Meaning are you on a 32bit system or a 64bit and did you download the right driver?

P.S. didn't see the other posts. There was a complex debian how to maybe I can check there.

---

### Post by Aximilli on 2006-05-14
the driver i have is ati-driver-installer-8.24.8-x86.run, which is the only non-64 bit installer they offer for radeons, other then the xwindows versions. I am on a 32 bit system.

---

### Post by Aximilli on 2006-05-14
So I ran the other version of the installer that doesn't ask for the distro, and it ran fine, then told me after installing to run aticonfig. I try to run it and get this.

 sudo aticonfig
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

I'm at a loss

---

### Post by catlett on 2006-05-14
Try this in the terminal ```
sudo apt-get install libfglrx_pp.so.1
``` With any luck it will install that library and you can rerun the installer.

---

### Post by Aximilli on 2006-05-14
I ran that code and got this output:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libfglrx_pp.so.1

---

### Post by catlett on 2006-05-14
F@!# that stinks. It seems like you need that package to install the ATI driver and it is not in the Ubuntu repositories. I'll try to google it and see if there is somewhere else to get it.

---

### Post by Aximilli on 2006-05-14
well i did check symantec package manager and there were files in there that looked like drivers, but they don't do jack for me once i install them.

---

### Post by catlett on 2006-05-14
I found this 
> 

Download the ATI driver installer: 32bit Installer

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps. Sample sources.list.

Install necessary tools:

sudo apt-get install gcc-3.4 module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

Create .deb packages:

chmod +x ati-driver-installer-8.24.8-x86.run
LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy

Install .deb packages:

sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb

Remove any old fglrx deb's from /usr/src/:

sudo rm /usr/src/fglrx-kernel*.deb

Compile the kernel driver:

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx

Update the xorg.conf file:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Reboot.
[edit]
Confirm that it worked

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)

(renderer string depends on your hardware and may/will be different)
[edit]
Troubleshooting
[edit]
General

Look for error messages in /var/log/Xorg.0.log and kern.log.
[edit]
Madwifi Drivers in Breezy Badger

In order to continue using the madwifi driver you can do the following before removing the linux-restricted-modules package and rebooting.

sudo cp /lib/modules/$(uname -r)/volatile/ath_hal.ko /lib/modules/$(uname -r)/kernel/
sudo depmod -a $(uname -r)

Retrieved from "http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide"

Category: Installation Documentation
Here [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

It's a bit long but the other way isn't working. Go to the website to read it all. This is part of a bigger guide and the links in this aren't showing up.

---

### Post by Aximilli on 2006-05-14
I'v been to this page several times, and I keep getting hung up with the very first command:

sudo apt-get install gcc-3.4 module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant

I'm almost ready to give up and just turn off my other monitor when i'm not on XP. But it would be nice to up the screen resolution a bit.

---

### Post by catlett on 2006-05-14
You might have to add a debian repository or add the universe and multiverse repos in ubuntu. I'll give a quick check

P.S. Have you added the universe repositories, etc.. The how to says you need to. follow this and try the commands again [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Aximilli on 2006-05-14
[QUOTE=catlett]You might have to add a debian repository or add the universe and multiverse repos in ubuntu. I'll give a quick check

P.S. Have you added the universe repositories, etc.. The how to says you need to. follow this and try the commands again [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]

I havent done anything with repositories. I don't even know what all that universe and multiverse mumbo jumbo is. But know I have another avenue to go down. I'll look into it later. Thank you very much for your help

Alex

---

### Post by Aximilli on 2006-05-15
So, a day later, I'v finally added the repositories I needed, and I'v been going through that help file you posted, and i get halfway down before I come across this error:

```
sudo rm /usr/src/fglrx-kernel*.deb
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory

```

should I continue?

---

### Post by telepheedian on 2006-05-15
You should also try Easy Ubuntu or Automatix, I'm not sure about ATI but Automatix did a great job installing my legacy Nvidia.

---

### Post by catlett on 2006-05-15
Do not add this command ```
sudo rm /usr/src/fglrx-kernel*.deb
```
That is a command to remove an old fglrx-kernel. But you don't have it. Make sure you follow the link to where that page came from. It has more detail and that page has links in it that didn't show up when I copied it.

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

---

### Post by Aximilli on 2006-05-16
So I finished the install, and now have the ati control panel working. However, when i tell it to enable split screen, I have to restart xsession, and once I do the changes seem to be discarded. I'v gone from having my second monitor just clone my first to it not showing anything. Anyone have and Ideas?

Thanks so much for all the support,
Alex

---

