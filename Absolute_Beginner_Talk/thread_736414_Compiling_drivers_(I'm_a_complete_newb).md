---
title: "Compiling drivers (I'm a complete newb)"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Seanross on 2008-03-26
we have about 4 computer in the house... 2 Desktops, 2 laptops... I manage all of them for the household, the wireless networks, etc. Been using windows since as long as I can remember(youngest I can remember is 8) so I'm somewhat fairly knowledgeable when it comes to windows. Always knew about Linux but just  stayed away because I knew enough to run windows without gettin viruses so it did the job well enough for me.

I tried the preview of the live cd on my laptop and liked it, then installed Ubuntu 7.10 on the older desktop in the house thats mostly used just for browsing. It has a Linksys WUSB54G Wireless adapter that it was using to access the network when it was running windows. I found the drivers for linux ([http://forums.driverguide.com/showthread.php?t=23488](http://forums.driverguide.com/showthread.php?t=23488)), and I understand I have to compile them somehow... 

I've been reading tutorials all about the place but i still feel dumb after reading them I understand I have to do the  (./configure, make, make install) process but where?I tried the terminal, root terminal, synaptics, etc..
 I opened up the folder after extracting the .tar.gz onto the desktop and started typing them in but getting no where of course. Is there a compiler I have to download and get onto the computer? 

Ubuntu looks nice and runs snappier than the Windows XP that was on the system, I hate to go back to Windows because of this little hangup, I'm trying to expose the family to something other than Windows.

---

### Post by markharding557 on 2008-03-26
this is based on a ralink 2500 chipset so there is a good chance it will work by default on ubuntu if not then you could use ndiswrapper there are plenty of threads about it.
one piece of advice get your support on ubuntu forums because it is specific to ubuntu and you will get more applicable advice good luck

---

### Post by Paqman on 2008-03-26
> **Seanross said:**
>  Is there a compiler I have to download and get onto the computer? 


Yes. You need to download a package called build-essentials. Then unzip your tar.gz, navigate to the unzipped folder in the terminal (the nautilus extension nautilus-open-terminal is handy for this) and execute those commands. If there's any kind of readme or instructions in the unzipped folder take a quick look, in case there's special instructions in there.

---

### Post by fela on 2008-03-26
first, you will need a package called build-essential, install it by keying into terminal: ```
sudo apt-get install build-essential
``` and hitting enter.

right. download and extract the source code .tar.gz (tarball) into a folder on your desktop. In this tutorial/howto i'm going to substitude whatever the name of that folder is for 'drivername'. Then, in terminal, key in: ```
cd Desktop/drivername
``` then ```
./configure
``` If configure succeeds (more on this later) go ahead and type ```
make
``` Loads of text might appear down the terminal. Don't panic! If THAT succeeds (if you see the user@hostname:$ prompt again after make has finished), type ```
sudo make install
``` That should install it. Restart X by typing ctrl+alt+backspace (or reboot depending on what the driver is), and it should work.

If ./configure fails asking for a dependency (e.g. Error: libwhatever needs to be installed), then you can try installing that library by typing [CODE]sudo apt-get install  in terminal.

Keep me posted :)

---

### Post by fela on 2008-03-26
Paqman, that's funny we gave exactly the same instructions at the exact same time...:lolflag:

---

### Post by zeronothing on 2008-03-26
you may need to download the build essentials package from synaptic. open up synaptic and search for build-essentials and install the package. also you can install the same package from terminal by typing:

sudo apt-get install build-essentials

 once you have that install you will have all of the nessesary programs to compile the drivers. as you mentioned before, with the file downloaded and extracted. you will need to open up termainal and change to that directory using the "cd" command (cd is the change directory command).

remember the "man" command is one of your best friends if you dont know what a particular command does in linux. to use the "man" command (which by the way is the manual command) works by using the command "man" followed by the command you need information for. ex/ "man ftp" and this command will display information regarding ftp commands.

hope this helps

---

### Post by TheWizzard on 2008-03-26
i don't think you'll need to compile the drivers. the Linksys WUSB54G is quite common. 
i'm sure the drivers are in the repo's. please note that there is somewhere in the setting an option to install propiarity drivers. 

take a look at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Seanross on 2008-03-26
thanks for all the replies... I'll try it all and report back

---

### Post by TheWizzard on 2008-03-27
> **Seanross said:**
> thanks for all the replies... I'll try it all and report back

one more thing. if you compile from source i'd advice you to use checkinstall. 
with checkinstall you can make a deb file and this way it is possible to add it to the dpkg database.

---

### Post by Seanross on 2008-03-27
I got the build essentials installed and I found Ndiswrapper and installed it too.. but I have no idea how to find it... I felt like I was getting somewhere with your help, somewhat close but no cigar

Here are the build instructions though that came with the source files


> 

Build Instructions:  
====================
0) $dos2unix *
      $chmod 644 *
      $chmod 755 Configure

1) cp Makefile.x Makefile               // x is your kernel

2) $make
3) $insmod rt2570.ko     # Insert driver module
4) $ifconfig rausb0 up  # Bring up device 
5) $dhclient rausb0  # Get network IP address

  Note: Script functionality:
  Configure       retrive linux version 
6) ./LINUX_RACONFIG_Vx.x.x.x/bin/"Linux"/RaConfig2500

if lack of libstdc++.so.6, cp ./LINUX_RACONFIG_Vx.x.x.x/libstdc++.so.6 /usr/lib

7)Edit(or add the line) in /etc/modules.conf
   alias rausb0 rt2570

8) Create and edit 'ifcfg-rausb0' file in /etc/sysconfig/network-script/
   DEVICE='rausb0'
   ONBOOT='yes'
   BOOTPROTO='dhcp' 

---

### Post by Seanross on 2008-03-28
bump

---

### Post by TheWizzard on 2008-03-28
> **Seanross said:**
> bump

[http://www.google.nl/search?q=Linksys+WUSB54G+ubuntu](http://www.google.nl/search?q=Linksys+WUSB54G+ubuntu)

---

### Post by Seanross on 2008-03-31
Thanks for all your help guys, but m just gonna install a modified version of windows xp back onto the computer. sorry for all the trouble:-k

---

