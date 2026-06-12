---
title: "Can't connect to wireless internet."
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by gaz2050 on 2008-03-24
Hi guys, I'm an absolute newbie to this so please be gentle, I've done a search for my problem and read the prompted threads for this thread, anyways....

I can't connect to the internet wirelessly. I've tried installing build-essential_11.3ubuntu1.tar but that tells me to insert a cd. :/ I don't really kno what I'm doing with this at the moment so if someone can send me a 'for dummies' guide that would be helpfull/ I'm using a buffalo wireless-G usb adapter if that's of any use. If there's any more information you need to know, just let me know.

Thanks in advance.

---

### Post by dstew on 2008-03-24
Hi gaz. First we need some information. What kind of computer is it? Which Ubuntu version do you have? Do you have a wired internet connection that can be used to download software and drivers?

You are probably going to need to use the ndiswrapper program to get that adapter to work. So, if you have a wired connection, go ahead and install ndiswrapper using the synaptic package manager (System --> Administration --> Synaptic Package Manager). Use the Search menu to look for and install the packages ndiswrapper-utils and ndiswrapper-common. You do not need to compile ndiswrapper from source as it seems you were preparing to do. But, if you do want to compile programs from source, you can install the build-essential package using synaptic too.

---

### Post by ichbinesderelch on 2008-03-24
could you pls postthe output of ifconfig, iwconfig and what wireless card you are using!

---

### Post by gaz2050 on 2008-03-25
It's a Compaq P.C, running off Ubuntu v7.10. I don't have a wired  'net connection but I'm dual booting so I can use windows xp for the internet (That's what I'm doing now :) ) I've just installed ndiswrapper ( Ithink) but that hasn't seemed to have done anythin. 

I'm not sure on how to get the ifconfig and iwconfig out put, as I say, I'm a complete newbie to this, and I also don't know what wireless card i'm using or how to find out :(

---

### Post by superprash2003 on 2008-03-25
once you type ifconfig in your terminal just highlight the output in the terminal.. then right click and click on copy and then right click and paste it here

---

### Post by dstew on 2008-03-25
> I'm using a buffalo wireless-G usb adapterThis adapter should work with kernel versions 2.6.23 and above. However, to get it to work with earlier kernels may be difficult. You can check your kernel version by entering the command```
uname -r
```

To use the command line, go to Applications --> Accessories --> Terminal. You enter the commands by typing them in an hitting enter. Also, post the output of ifconfig and iwconfig commands too, as recommended by ichbin.

---

### Post by gaz2050 on 2008-03-25
This is what I've managed  to come up with:

> gaz@Gaz2050:~$ uname -r
2.6.22-14-generic
gaz@Gaz2050:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

gaz@Gaz2050:~$ ipconfig
bash: ipconfig: command not found
gaz@Gaz2050:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:F2:42:49:E7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by gaz2050 on 2008-03-25
I don't know if this is any use but :

gaz@Gaz2050:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:00.0 Ethernet controller: Agere Systems ET-131x PCI-E Ethernet Controller (rev 01)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
gaz@Gaz2050:~$

---

### Post by dstew on 2008-03-25
It looks like you will need to try ndiswrapper. I haven't been able to find anyone that used ndiswrapper successfully with this dongle, so maybe you are the pioneer. It seems your kernel version is one shy of what is needed. You could try and build a custom kernel, or wait for the next Ubuntu kernel update (maybe a few months??)

If you want to try ndiswrapper, and you don't have an internet connection on your Ubuntu system, you are going to have to download program packages and driver files on your WIndows system, and transfer them to Ubuntu for installation. Are you willing to do that?

First, see if you have ndiswrapper installed on ubuntu yet. On a command line, enter```
ndiswrapper --help
```If ndiswrapper is installed, it will give you a list of options you can use. If ndiswrapper is not installed, you can get the pre-compiled Ubuntu Gutsy packages from the Ubuntu Packages site. Here are the links for [ndiswrapper-common]("http://packages.ubuntu.com/gutsy/ndiswrapper-common") and [ndiswrapper-utils]("http://packages.ubuntu.com/gutsy/ndiswrapper-utils-1.9") for Gutsy (7.10). The package files will have .deb extensions. Transfer them to your Ubuntu system. If you put them on the desktop, you can install them by changing to your Desktop folder, and issuing the dpkg command```
cd ~/Desktop
sudo dpkg -i ndiswrapper-common_1.43-1ubuntu2_all.deb
sudo dpkg -i ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb
```

---

### Post by gaz2050 on 2008-03-26
gaz@Gaz2050:~$ sudo lshw -C network
[sudo] password for gaz:
  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:15:f2:42:49:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x latency=0 module=et131x multicast=yes




gaz@Gaz2050:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:15:f2:42:49:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x latency=0 module=et131x multicast=yes


gaz@Gaz2050:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

gaz@Gaz2050:~$ cd ~/Desktop
gaz@Gaz2050:~/Desktop$ sudo dpkg -i ndiswrapper-common_1.43-1ubuntu2_all.deb
(Reading database ... 90731 files and directories currently installed.)
Preparing to replace ndiswrapper-common 1.43-1ubuntu2 (using ndiswrapper-common_1.43-1ubuntu2_all.deb) ...
Unpacking replacement ndiswrapper-common ...
Setting up ndiswrapper-common (1.43-1ubuntu2) ...
gaz@Gaz2050:~/Desktop$ sudo dpkg -i ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb 

This is what I've got from some of those commands. By the looks on things (although I'm probably wrong) NDISwraper doesn't support my dongle. Is there an alternative out there? 

I'd be willing to install and so whatever needs to be done to get the intrnet working on Ubuntu.

Wheredo I go from here please?

---

### Post by dstew on 2008-03-26
Well, you are only part way through the configuration process. You have installed ndiswrapper, that is all. Ndiswrapper is only a "wrapper" for the Windows driver that runs the card. Now, you need to install the Windows driver into ndiswrapper.

You first need to get the Windows driver for your adapter. Do you have the driver disk that came with it? If not, we can probably find it on-line. To show exactly what your USB dongle is, enter the command```
lsusb
```

---

### Post by gaz2050 on 2008-03-26
I have both the windows xp disk and the ubuntu 7.10 disk. I'll type the lsusb command now.

---

### Post by gaz2050 on 2008-03-26
gaz@Gaz2050:~$ lsusb
Bus 003 Device 003: ID 0411:00bc MelCo., Inc. 
Bus 003 Device 002: ID 1058:1001 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Western digital is my external hard drive's name.

---

### Post by dstew on 2008-03-26
OK, here is [the link to a .zip file that contains the Windows driver]("http://buffalotech.com/support/getfile/?U2KG125S.zip") for that device (the device ID is 0411:00bc). Copy the zip file to your desktop and un-zip it. You should get a folder named U2KG125S on your desktop.

From the command line, change your active directory to that folder, then install the driver into ndiswrapper:```
cd ~/Desktop/U2KG125S
ls -l
sudo ndiswrapper -i NETG125S.INF
```The names are case-sensitive, so check the correct names in the directory output first. If you do not get an error message, do```
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
```Hopefully your dongle will work now. Please post the output of these commands if you have trouble.

---

### Post by gaz2050 on 2008-03-26
gaz@Gaz2050:~$ cd ~/Desktop/U2KG125S
gaz@Gaz2050:~/Desktop/U2KG125S$ ls -l
total 120
-r-x------ 1 gaz gaz     4 2005-01-18 20:01 BCM43XX.CAT
-r-x------ 1 gaz gaz 33708 2006-04-06 21:04 NETG125S.INF
-r-x------ 1 gaz gaz 27264 2005-01-18 20:01 RNDISMPK.SYS
-r-x------ 1 gaz gaz 27264 2005-01-18 20:01 RNDISMP.SYS
-r-x------ 1 gaz gaz 11136 2005-01-18 20:01 USB8023K.SYS
-r-x------ 1 gaz gaz 11136 2005-01-18 20:01 USB8023.SYS
gaz@Gaz2050:~/Desktop/U2KG125S$ sudo ndiswrapper -i NETG125S.INF
[sudo] password for gaz:
installing netg125s ...
forcing parameter IBSSGMode from 0 to 2
gaz@Gaz2050:~/Desktop/U2KG125S$ ndiswrapper -l
netg125s : invalid driver!
gaz@Gaz2050:~/Desktop/U2KG125S$ sudo depmod -a
gaz@Gaz2050:~/Desktop/U2KG125S$ sudo modprobe ndiswrapper

It doesn't seem to have worked :(

---

### Post by dstew on 2008-03-26
See [this thread]("http://ubuntuforums.org/archive/index.php/t-370589.html"). Apparently you have to copy the RNDISMP.SYS and USB8023.SYS files to the directory /etc/ndiswrapper/netg125s/:```
sudo cp RNDISMP.SYS /etc/ndiswrapper/netg125s/
sudo cp USB8023.SYS /etc/ndiswrapper/netg125s/
```Then try ndiswrapper -l again.

---

### Post by gaz2050 on 2008-03-26
I've tried to paste the files into the directory but it says I don't have permission. I tried right clicking in the /etc/ndiswrapper/netg125s/: file but the paste icon didn't show, then I tried the drag and drop method and a window popped up saying I didn't have authorization.

Here's the codes I've got now:

-

gaz@Gaz2050:~$ sudo cp RNDISMP.SYS /etc/ndiswrapper/netg125s/
[sudo] password for gaz:
cp: cannot stat `RNDISMP.SYS': No such file or directory
gaz@Gaz2050:~$ sudo cp RNDISMP.SYS /etc/ndiswrapper/netg125s/
cp: cannot stat `RNDISMP.SYS': No such file or directory
gaz@Gaz2050:~$ sudo cp USB8023.SYS /etc/ndiswrapper/netg125s/
cp: cannot stat `USB8023.SYS': No such file or directory
gaz@Gaz2050:~$ sudo cp RNDISMP.SYS /etc/ndiswrapper/netg125s/
cp: cannot stat `RNDISMP.SYS': No such file or directory
gaz@Gaz2050:~$ sudo cp USB8023.SYS /etc/ndiswrapper/netg125s/
cp: cannot stat `USB8023.SYS': No such file or directory

---

### Post by dstew on 2008-03-26
> p: cannot stat `RNDISMP.SYS': No such file or directoryYou need to be in the driver directory for the command to work as I wrote it. If you are in your home directory, the commands would be```
sudo cp Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/
sudo cp Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/
```

---

### Post by Ketson on 2008-03-26
i seem to be havng a similar problem as above i have a wireless card built within my laptop an acer 7520. here is a bit of info that might help

ketson@lappytop:~$ uname -r
2.6.24-12-generic
ketson@lappytop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ketson@lappytop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:4c:7d:a8  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe4c:7da8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57715481 (55.0 MB)  TX bytes:2577112 (2.4 MB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5700 (5.5 KB)  TX bytes:5700 (5.5 KB)

---

### Post by gaz2050 on 2008-03-27
Ok this is the part where I'm getting confused now.I'm not sure how to get into the driver sirectory. Would me just using the desktop directory with the codes you kindly provided work?

---

### Post by dstew on 2008-03-27
Gaz, what you need to do is copy files from the drivers folder on you desktop to the /etc/ndiswrapper/netg125s folder that ndiswrapper uses. When you use the command line, you are aways "in" some directory somewhere. You usually start out in your home directory. The symbol for your home directory is ~, and its name is /home/gaz. You can always find out what directory you are in using the pwd command (Print Working Directory).

Anyway, you can also make a universal command that will work no matter what directory you are currently in. You just need to include the full path names for the source and targets. Here are commands that will work from anywhere:```
sudo cp ~/Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/
sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/
```If it doesn't work, post the error you get.

By the way, a good resource on basic linux command line skills is [here]("https://help.ubuntu.com/community/UsingTheTerminal").

---

### Post by gaz2050 on 2008-03-27
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/
[sudo] password for gaz:
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/sudo cp ~/Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/
cp: cannot stat `/etc/ndiswrapper/netg125s/sudo': No such file or directory
cp: cannot stat `cp': No such file or directory
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/sudo cp ~/Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/
cp: cannot stat `/etc/ndiswrapper/netg125s/sudo': No such file or directory
cp: cannot stat `cp': No such file or directory
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/pwd
gaz@Gaz2050:~$ pwd
/home/gaz
gaz@Gaz2050:~$ 

I'm not getting it :( What am I doing wrong? *cries*

---

### Post by dstew on 2008-03-27
Nothing. The command worked the first time you used it. The second command is just typed wrong:> gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/sudo cp ~/Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/You put two commands on one line, so it thought that /etc/ndiswrapper/netg125s/sudo was supposed to be a directory or file, and that 'cp' was supposed to be a directory or file, which it could not find. The command should be:```
sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/
```Each command is a separate line.

---

### Post by gaz2050 on 2008-03-27
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/
[sudo] password for gaz:
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/RNDISMP.SYS /etc/ndiswrapper/netg125s/
gaz@Gaz2050:~$ sudo cp ~/Desktop/U2KG125S/USB8023.SYS /etc/ndiswrapper/netg125s/

Still no internet :(

---

### Post by dstew on 2008-03-27
OK, now do```
ndiswrapper -l
```to see if the driver is working.

---

### Post by gaz2050 on 2008-03-27
gaz@Gaz2050:~$ ndiswrapper -l
netg125 : invalid driver!
netg125s : invalid driver!

---

### Post by dstew on 2008-03-27
Look first to see if the files were copied to the /etc/ndiswrapper/netg125s directory:```
ls -l /etc/ndiswrapper/netg125s
```

---

### Post by gaz2050 on 2008-03-28
gaz@Gaz2050:~$ ls -l /etc/ndiswrapper/netg125s
total 92
-rw-r--r-- 1 root root   692 2008-03-26 20:25 0411:00BC.F.conf
-rw-r--r-- 1 root root 33708 2008-03-26 20:25 netg125s.inf
-r-x------ 1 root root 11136 2008-03-27 17:30 pwd
-r-x------ 1 root root 27264 2008-03-27 19:41 RNDISMP.SYS
-r-x------ 1 root root 11136 2008-03-27 19:42 USB8023.SYS
gaz@Gaz2050:~$

---

### Post by dstew on 2008-03-28
OK, the .inf file wants to look for the system files using lower-case names. So, change the names of the files this way:```
sudo mv /etc/ndiswrapper/netg125s/RNDISMP.SYS /etc/ndiswrapper/netg125s/rndismp.sys
sudo mv /etc/ndiswrapper/netg125s/USB8023.SYS /etc/ndiswrapper/netg125s/usb8023.sys
```

---

### Post by gaz2050 on 2008-03-28
gaz@Gaz2050:~$ sudo mv /etc/ndiswrapper/netg125s/RNDISMP.SYS /etc/ndiswrapper/netg125s/rndismp.sys
[sudo] password for gaz:
gaz@Gaz2050:~$ ndiswrapper -l
netg125 : invalid driver!
netg125s : driver installed
        device (0411:00BC) present
gaz@Gaz2050:~$

---

### Post by dstew on 2008-03-28
Ah, progress. I don't know if you have to remove the netg125 "driver" from ndiswrapper, but the netg125s driver is working. To remove the false driver, do```
sudo ndiswrapper -r netg125
```Now do ```
sudo depmod -a
sudo modprobe ndiswrapper
iwconfig
```

---

### Post by gaz2050 on 2008-03-28
netg125
[sudo] password for gaz:
couldn't delete /etc/ndiswrapper/netg125: No such file or directory
gaz@Gaz2050:~$ sudo depmod -a
gaz@Gaz2050:~$ sudo modprobe ndiswrapper
gaz@Gaz2050:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Auto  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Link Quality:100  Signal level:0  Noise level:160
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gaz@Gaz2050:~$ 



It's probably worth noting my computer froze a couple of times when I typed in the command and the keyboard lights started flashing. I also had problems saving the text document. A few restarts sorted it but obviously I'd like it to be prevented.

---

### Post by dstew on 2008-03-28
Does the system lock up when you do modprobe ndiswrapper? Try it again from the top and see:```
sudo depmod -a
sudo modprobe ndiswrapper
```If it does not lock up, open the network configuration window (System --> Administration --> Networking) and see if the wlan0 interface is there.

---

### Post by gaz2050 on 2008-03-28
It froze after the modprobe ndiswrapper command. The depmod -a command didn't appear to do anything. At least nothing showed up in the terminal, it just went to a new command line. I just restarted the computer in XP so I'm not sure if the wlan0 interface is there. Shall I check that now?

---

### Post by dstew on 2008-03-28
> I'm not sure if the wlan0 interface is there. Shall I check that now?No, don't bother. If it froze when you did modprobe ndiswrapper, that means that the version of ndiswrapper does not match the version of the kernel (core of the operating system). My fault, I should have checked before installing ndiswrapper. Anyway, we know we have a working driver.

So, lets check the ndiswrapper version and the kernel version. Then we will decide what to do about it. Here are the codes. To check the kernel version:```
uname -r
```To check the ndiswrapper version:```
ndiswrapper -v
```We might need to get a different version of ndiswrapper to work with your kernel.

Are you able to connect your Ubuntu computer to the internet by a wired connection? That might help us to update your system, which might help if we can get a kernel update too.

---

### Post by gaz2050 on 2008-03-29
gaz@Gaz2050:~$ uname -r
2.6.22-14-generic
gaz@Gaz2050:~$ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 
gaz@Gaz2050:~$ 


Unfortunately I'm not able to connect to the internet with a wire :(

---

### Post by dstew on 2008-03-29
Here is what I am thinking. The ndiswrapper version 1.45 has a bug in it that causes the kernel to crash whenever it is loaded. The fix is to upgrade to a newer version of ndiswrapper, or perhaps to the upgrade the kernel.

To upgrade these items (really update might be a better word) the usual practice is to get the Ubuntu-packaged updates using the Update Manager found in the System --> Administration menu. Unfortunately, you need an internet connection to do this. And, I am not even sure if an update would get you a newer version of ndiswrapper or your kernel.

There is a way to update off-line. You can use the service [nonetdebs]("http://nonetdebs.homeip.net/"). You sign up for their service, and upload to them a file that shows the current state of your machine, and they assemble for you an update package that you can download on another machine, burn to a CD or put on a USB stick, and then install on your Ubuntu machine. I suggest you do this.

After you update, if ndiswrapper still causes the kernel to crash, the only way forward would be to compile a newer ndiswrapper program from source. That is not hard, but you will need to install some packages to get ready to do that. Again, you can probably use nonetdebs to get the packages to install. If you just tried to download individual packages, you would have trouble satisfying all the dependencies (gettting the packages that the packages need).

---

### Post by gaz2050 on 2008-03-29
Thanks for that. I've signed up and uploaded on the nonetdebs site. Just wondering though, would a different distribution of linux solve the wireless internet problem or would they all struggle with my adapter?

---

### Post by gaz2050 on 2008-03-29
Sorry for the doublt post but under the new packages section it says 
> STOP: No package to install/list !!!!
Please edit your account and type a package to list and install on the target.

I don't know what to do about his either :(

---

### Post by dstew on 2008-03-29
I've never used nonetdebs, so I don't know if there is a problem, or if you just don't have anything that needs updating. Check [this how-to]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11"), and see if you need to do anything more to get your packages. For example, did you click "Submit" after you clicked "Upload" to upload your status.txt file?

EDIT:> would a different distribution of linux solve the wireless internet problemVery probably. You are trying to work with a fairly buggy distribution. For example, your card might work fine with Dapper Drake 6.06 or Feisty Fawn 7.04, and might work fine with Hardy Heron 8.04 whenever that is ready for final release. And, other distributions like Slackware or Mint might work better too.

---

