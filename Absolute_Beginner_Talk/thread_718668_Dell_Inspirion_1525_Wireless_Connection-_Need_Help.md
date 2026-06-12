---
title: "Dell Inspirion 1525 Wireless Connection- Need Help!"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2008-03-08
Just installed Gutsy and it does NOT recognize my wireless network.  It's a 32 bit machine, with Dell Wireless 1505 Wireless-N Mini-card. 

I'm issuing this plea from my desktop.  I reviewed plenty of theads, but since I'm an absolute novice at this, few make sense.

My router is a Linksys wireless-G.  Works fine in Vista.

Please help!

---

### Post by hyperair on 2008-03-08
Could you post the output of this:
```
lspci -nn
```

---

### Post by jan quark on 2008-03-08
please post the output from these terminal commands:


```
sudo lshw -C network
```

```
iwconfig

```

---

### Post by Aurora@FleetBuzz on 2008-03-08
For sudo lshw -C network:

> donj@donj-laptop:~$ sudo lshw -C network
[sudo] password for donj:
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:44:e6:bd
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

For iwconfig:
l> o        no wireless extensions.

eth0      no wireless extensions.


For lspci -nn:
> donj@donj-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)


Thanks for the responses.  I'm on line via ethernet.

---

### Post by Aurora@FleetBuzz on 2008-03-08
Anyone?  Help!

---

### Post by Aurora@FleetBuzz on 2008-03-08
I found out that my card has a Broadcom 4328 chipset.  I also found this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

I thought these instructions were promising:
> Internet Enabled Installation

This procedure is the simplest, but requires an Internet connection.

1) Open System -> Administration -> Restricted Driver Manager and you will see that under the Firmware drop down arrow it says Firmware for Broadcom 43xx chipset family and under Status it says Not in Use.

2) Tick the box under Enabled to enable the firmware.

3) Click Enable Firmware to continue and the bcm43xx-fwcutter package will be installed. If you receive a time out error message then you may need to switch to a different repository mirror or try the off-line install further down this page.

4) Select Download from the Internet to proceed using the pre-filled URI or select a local file if you prefer.

5) Click Ok to extract the firmware.

6) If the Status has changed to In use, then you are successful. 

However, Ubuntu tells me that I have no need of restricted drivers!

---

### Post by ghost_ryder35 on 2008-03-08
Youll need to plug an ethernet cable into your laptop for this one....

sudo apt-get install bcm43xx-fwcutter
sudo modprobe bcm43xx
then restart computer and all is good
iwconfig to check

---

### Post by Aurora@FleetBuzz on 2008-03-08
Thanks!  I'll try now.

Do I need to uninstall NDISwrapper or anything?

---

### Post by ghost_ryder35 on 2008-03-08
yes

---

### Post by Aurora@FleetBuzz on 2008-03-08
Too late!

I did the install without uninstalling NDISwrapper.  Will it still work if I remove and reboot?

---

### Post by ghost_ryder35 on 2008-03-08
yeppers.  It will work, doesnt matter at what point you uninstall ndiswrapper.  Post and let us know.  I will be on for another 30minutes

---

### Post by Aurora@FleetBuzz on 2008-03-08
Unfortunately, iwcongig is still showing:
> o no wireless extensions.

eth0 no wireless extensions.:(
I restarted and there is no "Wireless" connection in the Network Settings configuration box.  Safe to say it's still not recognizing the wireless card.

Perhaps I missed a step?

---

### Post by ghost_ryder35 on 2008-03-08
maybe need to black list the ndiswrapper drivers.   I am rusty at blacklistng....  let me do some quick research.  try a **modprobe bcm43xx** again and see if that works some magic....

---

### Post by ghost_ryder35 on 2008-03-08
Check to see what ndiswrapper modules are loaded:

**ndiswrapper -l**
if there are some, remove them with:
 
**ndiswrapper -e NAME_OF_MODULE**

---

### Post by Aurora@FleetBuzz on 2008-03-08
tr> y a modprobe bcm43xx again and see if that works some magic....sn'
Doesn't look too good....
> donj@donj-laptop:~$ modprobe bcm43xx
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko): Operation not permitted
WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted


---

### Post by Aurora@FleetBuzz on 2008-03-08
> **ghost_ryder35 said:**
> Check to see what ndiswrapper modules are loaded:

**ndiswrapper -l**
if there are some, remove them with:
 
**ndiswrapper -e NAME_OF_MODULE**

None left:
> The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found


---

### Post by ghost_ryder35 on 2008-03-08
do a **sudo modprobe bcm43xx** ;)  Operation is not permitted because you are not the root user

---

### Post by Aurora@FleetBuzz on 2008-03-08
> **ghost_ryder35 said:**
> do a **sudo modprobe bcm43xx** ;)  Operation is not permitted because you are not the root user

Just did and am rebooting....

---

### Post by Aurora@FleetBuzz on 2008-03-08
No luck.  I ran the command preceded by sudo.  It ran w/o comment, but when I rebooted Ubuntu still does not recognize a wireless network.

---

### Post by ghost_ryder35 on 2008-03-08
when you did the **sudo modprobe bcm43xx[B] did the blue wireless light turn on???**[/B]

---

### Post by lswest on 2008-03-08
try this: ```
gksudo gedit /etc/modules
``` then append to the end of the file the line "bcm43xx" and reboot.

---

### Post by ghost_ryder35 on 2008-03-08
are you booting in verbose mode?  Can you see the text scrolling when it boots???I wonder if the bcm43xx module is loading.  Try doing a **sudo modprobe bcm43xx** and not rebooting, but waiting about 5 minutes....

---

### Post by ghost_ryder35 on 2008-03-08
> **lswest said:**
> try this: ```
gksudo gedit /etc/modules
``` then append to the end of the file the line "bcm43xx" and reboot.

damn smart people :)

---

### Post by Aurora@FleetBuzz on 2008-03-08
You mean the blue light that indicates a wireless network (front left on my Inspiron 1525).  Its on.

---

### Post by ghost_ryder35 on 2008-03-08
> **Aurora@FleetBuzz said:**
> You mean the blue light that indicates a wireless network (front left on my Inspiron 1525).  Its on.


And your sure it is not picking up any wireless connections??????  Turn the computer off and let sit for 60 seconds to clear ram and reboot.  If the blue wireless light comes on then it is loading the module and there is something else that is the problem......

---

### Post by Aurora@FleetBuzz on 2008-03-08
That's what I'm trying now.  I also modified the file and appended bcm43xx at the end.  Here's hoping....

---

### Post by Aurora@FleetBuzz on 2008-03-08
Just rebooted and there's not only no wireless, but no blue light!

Should I try "sudo modspace ..." again?

---

### Post by ghost_ryder35 on 2008-03-08
yea run a **sudo modprobe bcm43xx** and wait 5 minutes.  After the 5 minutes (or less) the blue light should come on again.....

---

### Post by ghost_ryder35 on 2008-03-08
could also try **lsmod** and look for bcm43xx.  If it is listed there then it is loaded and running and the puzzle continues :)

---

### Post by ghost_ryder35 on 2008-03-08
Did it work?

---

### Post by Aurora@FleetBuzz on 2008-03-08
> **ghost_ryder35 said:**
> could also try **lsmod** and look for bcm43xx.  If it is listed there then it is loaded and running and the puzzle continues :)

Yes, it's there!  And...no blue light indicating the wireless is being detected.

---

### Post by ghost_ryder35 on 2008-03-08
It being listed there is good.  It not loading with the **sudo modprobe bcm43xx** and loading it into the file is not good.  I am pondering this question right now.  I am running it on a Inspiron 1520 right now.......

---

### Post by ghost_ryder35 on 2008-03-08
Try this....

1. Go to Synaptic Package manager and search for **BCM43XX-FWCUTTER**
2. Right click and Remove **BCM43XX-FWCUTTER **via Synaptic Package manager
3. Remove BCM43XX from /etc/modules by **gksudo gedit /etc/modules**
4. Shutdown computer and let sit for 60 seconds
5. Turn on computer
6. reissue the command
 **sudo apt-get install bcm43xx-fwcutter**
7.  Shutdown computer

---

### Post by Aurora@FleetBuzz on 2008-03-08
Shut down and re-start after 60 sec?

---

### Post by Aurora@FleetBuzz on 2008-03-08
> **ghost_ryder35 said:**
> Try this....

1. Go to Synaptic Package manager and search for BCM43XX
2. Right click and Remove BCM43XX via Synaptic Package manager
3. Remove BCM43XX from /etc/modules by **gksudo gedit /etc/modules**
4. Shutdown computer and let sit for 60 seconds
5. Turn on computer
6. reissue the command
 **sudo apt-get install bcm43xx-fwcutter**
7.  Shutdown computer

BCM43XX is not installed according to the synaptic.

bcm43xx-fwcutter is installed.

---

### Post by ghost_ryder35 on 2008-03-08
> **Aurora@FleetBuzz said:**
> Shut down and re-start after 60 sec?
Yea.  Essentially I am thinking something went wrong with the install somehow.  So we are removing it and reinstalling.  If the blue light came on even once then the DAMN thing was working and then decided to quit on us.... Wonder why...

---

### Post by ghost_ryder35 on 2008-03-08
> **Aurora@FleetBuzz said:**
> BCM43XX is not installed according to the synaptic.

bcm43xx-fwcutter is installed.

Oops.... Thats what I meant.  **bcm43xx-fwcutter**

Remove that one.

---

### Post by Aurora@FleetBuzz on 2008-03-08
> **ghost_ryder35 said:**
> Oops.... Thats what I meant.  **bcm43xx-fwcutter**

Remove that one.

Done.  Removed it via the synaptic.

Removed reference from /etc/modules

Reinstalled via the command line.

Restarting....

---

### Post by Aurora@FleetBuzz on 2008-03-08
Shut down and restarted.  Still no wireless.

BTW, I greatly appreciate your help and patience here!

---

### Post by ghost_ryder35 on 2008-03-08
Oops.  I wanted you to Remove it via Synaptic and remove the referece from /etc/modules and then shut down, wait 60 seconds, then boot up and install without the "sudo modprobe bcm43xx" then shutdown wait 60 seconds and then turn on......

---

### Post by ghost_ryder35 on 2008-03-08
No problems with the patience....I take it the blue light did not turn on.....  Let me get a link for you to a website

---

### Post by Aurora@FleetBuzz on 2008-03-08
I can revove via the synaptic again.

---

### Post by ghost_ryder35 on 2008-03-08
You probally will want to uninstall again before doing it this way...  Before doing this try issuing a "sudo modprobe bcm43xx" for shits and giggles.  I know this is getting annoyingly repeating.
"
Off-line Installation
This procedure outlines the process of downloading the neccessary installation files using a separate Internet enabled PC as an intermediary. If you have a working Windows partition, then you can use that to get the file you need and reboot into Ubuntu to finish the installation. 

**1**) Download the  bcm43xx-fwcutter package from the Universe repository. 

Intel compatible - [ bcm43xx-fwcutter_006-3_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb")

64 bit - [ bcm43xx-fwcutter_006-3_amd64.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_amd64.deb")

PowerPC -  bcm43xx-fwcutter_006-3_powerpc.deb 

**2**) Download the firmware from  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) or see Firmware Sources below. 

**3**) Transfer these files on to the Ubuntu machine. 

**4**) Double-click the bcm43xx-fwcutter-*.deb package to install with the package installer. You may receive a warning that there is the same version available from the channel, but as it's not currently accessible you will have to proceed with this file. 

**5**) During installation it will ask you if you would like it to fetch and extract the firmware. This step will fail without an Internet connection so just click Forward and then close the the package installer. 

**6**) Open System -> Administration -> Restricted Driver Manager and you will see that under the Firmware drop down arrow it says Firmware for Broadcom 43xx chipset family and under Status it says Not in Use. 

**7**) Tick the box under Enabled to enable the firmware. 

**8**) Click Enable Firmware to continue. 

**9**) Select Use a local file and browse to the wl_apsta-3.130.20.0.o firmware file and click Open. 

**10**) Click Ok to extract the firmware. 

**11**) If the status has changed to In use, then you are successful. 
"

---

### Post by Aurora@FleetBuzz on 2008-03-08
I'll give it a shot.

I can plug in the ethernet connection for step 5.  Do you recommend it?

---

### Post by ghost_ryder35 on 2008-03-08
> **Aurora@FleetBuzz said:**
> I'll give it a shot.

I can plug in the ethernet connection for step 5.  Do you recommend it?

NO, do not use the internet for this one.  That is why we are downloading the files our self...  Let me know, If I'm not on anymore shoot me a PM or something.  This should WORK!!!!!!!!!!!!!!  I can not figure it out other than something is going wrong with the downloaded files and or "I.B.T.K.A.C"  (dont ask what that stands for :))

---

### Post by Aurora@FleetBuzz on 2008-03-08
I'm again being told my hardware does not need restricted drivers, so I guess the firmware is installed, or it still does not recognize my wireless card?

---

### Post by ghost_ryder35 on 2008-03-08
GGGGGGGGGRRRRRRRRRRRRRRR!!!!!!!!!!!!!!!   Try hitting the "FN + F2"  in english that is the "Function key (on the keyboard) + Wireless key (on the keyboard)"  This would just let us make sure the bios has the wireless card turned on...

---

### Post by ghost_ryder35 on 2008-03-08
Well.... Since I am so stumped.... What happened to make NDISwrapper not work for you???

---

### Post by Aurora@FleetBuzz on 2008-03-08
BTW, the wireless light is back on!  I just re-booted.  No idea why.

---

### Post by Aurora@FleetBuzz on 2008-03-08
> **ghost_ryder35 said:**
> Well.... Since I am so stumped.... What happened to make NDISwrapper not work for you???

I actually only got as far as installing it!  I pulled it out when we started trying the other stuff.

---

### Post by ghost_ryder35 on 2008-03-08
> **Aurora@FleetBuzz said:**
> BTW, the wireless light is back on!  I just re-booted.  No idea why.

Then doing a **lsmod** should show "bcm43xx" running....  That means, well whatever....

Try this.....
I think your best bet would be to go back and use NDISwrapper.... 

You are going to have to remove **bcm43xx-fwcutter** via Synaptic and reboot.....
Then follow these instructions...

"Model of my wifi card is “Broadcom BCM4328 802.11a/b/g/n (rev 01)”

Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


sudo ndiswrapper -i /download_directory/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper


4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules


and add the following module to the list


ndiswrapper


5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi  )
"

---

### Post by Papa-san on 2008-03-09
OK... so did it work?
I have the same issue. My cards are the bcm4310 version 01 (3 identical laptops I'm trying to get working)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **Papa-san said:**
> OK... so did it work?

I'll let you know if a couple of hours.

---

### Post by ghost_ryder35 on 2008-03-09
> **Papa-san said:**
> OK... so did it work?
I have the same issue. My cards are the bcm4310 version 01 (3 identical laptops I'm trying to get working)

PAPA, you have the 4310 chipset, 

1. sudo apt-get update
2. sudo apt-get install bcm43xx-fwcutter
3. sudo modprobe bcm43xx
4. restart


THIS WILL WORK FOR YOU,

I am pretty sure Aurora@FleetBuzz is having problems because he has the new chipset bcm4328 V.3
Hopefully Aurora@FleetBuzz will unistall the BCM43XX-FWCUTTER module and blacklist bcm43xx, then use the method I posted for NDISwrapper.  This will make the wireless card work but with limited function such as no packet injection etc....

---

### Post by Aurora@FleetBuzz on 2008-03-09
BTW, my router is set for wireless (WPA) encryption.  Is that an issue?  It shouldn't be; on windows it merely asks for the key and all is well after that.

Getting ready to perform the operation you recommended with NDISwrapper....

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> BTW, my router is set for wireless (WPA) encryption.  Is that an issue?  It shouldn't be; on windows it merely asks for the key and all is well after that.

Getting ready to perform the operation you recommended with NDISwrapper....
no, it is not an issue.  

WPA works with NDISwrapper

---

### Post by Aurora@FleetBuzz on 2008-03-09
> 1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


sudo ndiswrapper -i /download_directory/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper




I downloaded the driver to my desktop.  Right clicked on the icon and clicked"extract here".  There is now a folder on my desktop called "151517.exe_files".  What is the syntaxt for the first command line?

**sudo ndiswrapper - /desktop/DRIVER/bcmwl5.inf** ?

---

### Post by ghost_ryder35 on 2008-03-09
sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf


****  there is a space after "bcmwl5." before "inf"  you need to remove it, for some reason it keeps going in there dont know why...


folders and everything is case sensitive, so desktop has to be Desktop

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf


folders and everything is case sensitive, so desktop has to be Desktop

I cut an pasted that line and executed.  This is the result:
> donj@donj-laptop:~$ sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5. inf
[sudo] password for donj:
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
donj@donj-laptop:~$ 


OK to proceed to the next line?

---

### Post by Aurora@FleetBuzz on 2008-03-09
Oops!  Forgot to remove the space!

Try again?

---

### Post by ghost_ryder35 on 2008-03-09
yes

---

### Post by Aurora@FleetBuzz on 2008-03-09
Unbelievable!  First it tells me the driver is installed; then after the second command it says "invalid driver".  I even ripped out NDISwrapper and installed everything again, re-booted and executed the first two commands!

> donj@donj-laptop:~$ sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf
[sudo] password for donj:
driver bcmwl5 is already installed
donj@donj-laptop:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
donj@donj-laptop:~$ 

I have not executed the last line....

---

### Post by Papa-san on 2008-03-09
Did you guys end up verifying that bcm43xx was blacklisted? I don't seem to remember if he looked at it... 

Just to be sure, ```
sudo gedit /etc/modprobe.d/blacklist
```When that opens, just scroll to the bottom and make sure one of the last entries is simply 'blacklist bcm43xx'.

---

### Post by ghost_ryder35 on 2008-03-09
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper

---

### Post by Aurora@FleetBuzz on 2008-03-09
Here's the result of the "blacklist" query:
> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

---

### Post by ghost_ryder35 on 2008-03-09
> **Papa-san said:**
> Did you guys end up verifying that bcm43xx was blacklisted? I don't seem to remember if he looked at it... 

Just to be sure, ```
sudo gedit /etc/modprobe.d/blacklist
```When that opens, just scroll to the bottom and make sure one of the last entries is simply 'blacklist bcm43xx'.
good reminder.  Definetly make sure it is blacklisted.  I think a good 
**sudo modprobe ndiswrapper** might help us out here to once we verify it is blacklisted

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> Here's the result of the "blacklist" query:
is that the whole blacklist?

---

### Post by jan quark on 2008-03-09
```
sudo gedit /etc/modprobe.d/blacklist
```

and add the line

```
blacklist bcm43xx
```
save and reboot

---

### Post by ghost_ryder35 on 2008-03-09
add
"** blacklist bcm43xx **"

---

### Post by Papa-san on 2008-03-09
> **Aurora@FleetBuzz said:**
> Unbelievable!  First it tells me the driver is installed; then after the second command it says "invalid driver".  I even ripped out NDISwrapper and installed everything again, re-booted and executed the first two commands!



I have not executed the last line....In the code you posted above, it looks like the space is still in front of the .inf if it would allow it to install, it would end up invalid that way...


(If I'm a bother, tell me to go away) Just tryin' to learn with ya! 
(You do have a BUNCH of us here watching and rooting for ya!)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **Papa-san said:**
> 
(If I'm a bother, tell me to go away) Just tryin' to learn with ya!
Not at all!  BTW, I removed the space the last time.

---

### Post by ghost_ryder35 on 2008-03-09
> **Papa-san said:**
> In the code you posted above, it looks like the space is still in front of the .inf if it would allow it to install, it would end up invalid that way...


(If I'm a bother, tell me to go away) Just tryin' to learn with ya!


No you are right, maybe we should uninstall the driver and reinstall without the space... still cant figure out why it wont go away

---

### Post by ghost_ryder35 on 2008-03-09
aurora you want to try uninstalling the bcmwl5.inf driver and reinstalling
I am not sure but I think an uninstall is **sudo ndiswrapper -r bcmwl5.inf**
[B]sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf

sudo modprobe ndiswrapper[/B]

---

### Post by ghost_ryder35 on 2008-03-09
the space still might be there, double check!

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> aurora you want to try uninstalling the bcmwl5.inf driver and reinstalling
I am not sure but I think an uninstall is **sudo ndiswrapper -r bcmwl5.inf**
[B]sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf

sudo modprobe ndiswrapper[/B]
This is what I got:
> couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory


Is this frustrating, or what!

Did the blacklist have anything to do with it?

---

### Post by ghost_ryder35 on 2008-03-09
LOL dude was right,
do this
**sudo ndiswrapper -r bcmwl5. inf**
i added the space

---

### Post by harold4 on 2008-03-09
Anyone gotten the N functionality of this card working with ndiswrapper?

---

### Post by ghost_ryder35 on 2008-03-09
> **harold4 said:**
> Anyone gotten the N functionality of this card working with ndiswrapper?
Once we get the card working we will let ya know ;)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> LOL dude was right,
do this
**sudo ndiswrapper -r bcmwl5. inf**
i added the space

Here's the result.  Was it zapped?
> donj@donj-laptop:~$ sudo ndiswrapper -r bcmwl5. inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
donj@donj-laptop:~$ 


---

### Post by Papa-san on 2008-03-09
This OS can be SO fussy... 

I learned the importance of something so small in one of my first threads (banged my head on the wall for TWO WEEKS because I didn't capitalize 'Desktop' in one of my steps...) And it will do just what you tell it to...

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> aurora you want to try uninstalling the bcmwl5.inf driver and reinstalling
I am not sure but I think an uninstall is **sudo ndiswrapper -r bcmwl5.inf**
[B]sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf

sudo modprobe ndiswrapper[/B]
Should I execute the last two lines?

---

### Post by ghost_ryder35 on 2008-03-09
do a **ndiswrapper -l** to see if it is listed as instaleld

---

### Post by ghost_ryder35 on 2008-03-09
finally we are getting somewhere.... let me know if it is still installed...

---

### Post by Aurora@FleetBuzz on 2008-03-09
This still remains to be accomplished.  Does the sequencing matter, or should I just do it?
> 4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules


and add the following module to the list


ndiswrapper


5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi )

---

### Post by ghost_ryder35 on 2008-03-09
when we reinstall it make sure there is no space.  it still might be there...

---

### Post by ghost_ryder35 on 2008-03-09
have you reinstalled it yet?

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> finally we are getting somewhere.... let me know if it is still installed...
Looks like it's gone....
> 
donj@donj-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!
donj@donj-laptop:~$ 

---

### Post by ghost_ryder35 on 2008-03-09
ok reinstall it using the above commands and make sure there is no space,
then do a sudo modprobe ndiswrapper

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> have you reinstalled it yet?
Reinstalled what?  I think I've lost my place!  It appears the driver has been zapped.  Could you direct me to the line to reinstall?  
(BTW, this is why I generally avoid the terminal.  GUI for me....):)

---

### Post by ghost_ryder35 on 2008-03-09
sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5. inf

sudo modprobe ndiswrapper


make SURE THERE IS NO SPACE

---

### Post by azimuth on 2008-03-09
At the risk of confusing the issue:  Dell had different versions of the same drive for 32 bit and 64 bit, for my bcm4311. Naturally I started with the wrong one and had much the same problems you are having. Just jot this down for reference. When you get to the point that it should be working and it isn't, double check that you have the right driver version.

ps They were both named bcmwl5

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5. inf

sudo modprobe ndiswrapper


make SURE THERE IS NO SPACE
Got this:
> donj@donj-laptop:~$ sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf
driver bcmwl5 is already installed
donj@donj-laptop:~$ sudo modprobe ndiswrapper
donj@donj-laptop:~$ 


---

### Post by ghost_ryder35 on 2008-03-09
is the wireless light on?

---

### Post by ghost_ryder35 on 2008-03-09
i also this there is a space again between bcmwl5.     and inf  make sure you removed it prior to installation

---

### Post by Papa-san on 2008-03-09
I copied and pasted that result in my own terminal, and could still delete the space between bcmwl5. and the inf...

Do that in your terminal before you hit enter...
Sure getting the 'Baptism by Fire' here!

---

### Post by ghost_ryder35 on 2008-03-09
> **Papa-san said:**
> I copied and pasted that result in my own terminal, and could still delete the space between bcmwl5. and the inf...

Do that in your terminal before you hit enter...

Yea I have no idea why I cant delete the space out of it.  I copied it and pasted into my terminal and deleted the space and then copy and pasted back into my post but it still was there.... So confusing!

---

### Post by Papa-san on 2008-03-09
Yeah... Don, you're going to need to be sure on your own_ after_ you cut and paste, before you enter.

OK... as the rest of this drama unfolds, I'm gonna get breakfast and start on my daughters system. I'll check back in a bit. 

(In the medical profession, we make sure to get another set of eyes on things that frustrate us, because we can miss stuff, even when it's right there... And I'll tell you,,, Linux is much fussier than human physiology!)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **Papa-san said:**
> I copied and pasted that result in my own terminal, and could still delete the space between bcmwl5. and the inf...

Do that in your terminal before you hit enter...
Sure getting the 'Baptism by Fire' here!
I cut and pasted it into the text editor, removed the space, cut and pasted it into the terminal.  Here is the result:
> donj@donj-laptop:~$ sudo ndiswrapper -i /home/donj/Desktop/151517.exe_files/DRIVER/bcmwl5.inf
driver bcmwl5 is already installed
donj@donj-laptop:~$ 

When I run modprobe, nothing happens.

When I try to uninstall the damn thing, I get this:
> donj@donj-laptop:~$ sudo ndiswrapper -r bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory


---

### Post by Aurora@FleetBuzz on 2008-03-09
> **Papa-san said:**
> Yeah... Don, you're going to need to be sure on your own_ after_ you cut and paste, before you enter.
I verified it twice!  There is no space when I entered it.  I'm almost at the point of uninstalling ndiswrapper and starting all over again!

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> I verified it twice!  There is no space when I entered it.  I'm almost at the point of uninstalling ndiswrapper and starting all over again!

you have a ethernet connection on this puppy????

Go to Add/Remove programs

and select all programs on the right drop down menu after it opens

then type "ndis"

Then downloaded the NDISwrapper gui interface.  Maybe this will help us out,

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> you have a ethernet connection on this puppy????

Go to Add/Remove programs

and select all programs on the right drop down menu after it opens

then type "ndis"

Then downloaded the NDISwrapper gui interface.  Maybe this will help us out,

Done.

How do I open it?

---

### Post by Papa-san on 2008-03-09
in terminal, its 'ndisgtk' (If that's the one you installed...) I believe it's default with ndiswrapper

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> Then doing a **lsmod** should show "bcm43xx" running....  That means, well whatever....

Try this.....
I think your best bet would be to go back and use NDISwrapper.... 

You are going to have to remove **bcm43xx-fwcutter** via Synaptic and reboot.....
Then follow these instructions...

"Model of my wifi card is “Broadcom BCM4328 802.11a/b/g/n (rev 01)”

Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


sudo ndiswrapper -i /download_directory/DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper


4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules


and add the following module to the list


ndiswrapper


5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi  )
"

Have done every step here and FN+ F2 does not turn on the wi-fi

---

### Post by ghost_ryder35 on 2008-03-09
dude I know the problem... LOL... I linked the wrong driver... I am so sorry..

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **Papa-san said:**
> in terminal, its 'ndisgtk' (If that's the one you installed...) I believe it's default with ndiswrapper
Thanks!

I opened it to be greeted by a message that" bcmwl5 is an invalid Driver!"
Remove and what . . .?

---

### Post by ghost_ryder35 on 2008-03-09
[http://ftp.us.dell.com/network/Dell_multi-device_A17_R174292.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174292.exe)

if that link doesnt work go here


[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R174292&SystemID=INS_PNT_PM_1525&servicetag=&os=WLH&osl=en&deviceid=14147&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236824](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R174292&SystemID=INS_PNT_PM_1525&servicetag=&os=WLH&osl=en&deviceid=14147&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236824)


follow the steps 

Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174292.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174292.exe) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


**sudo ndiswrapper -i /home/donj/Desktop/174292.exe_files/DRIVER/bcmwl5.inf  **(to install)
**sudo ndiswrapper -l **(to make sure it installed)
**sudo modprobe ndiswrapper** (to start)


4. Then, set ndiswrapper to load on startup:

sudo ndiswrapper -m
gksudo gedit /etc/modules


and add the following module to the list


ndiswrapper


5. Restart (This is a must)

Now you can use Fn+F2 to turn on your wifi )
"

---

### Post by ghost_ryder35 on 2008-03-09
I edited the above post with the proper driver (once again I am so sorry) and with the proper syntax of commands.  Once again double check the space problem.  Once you follow this though it should work perfectly fine.

---

### Post by Aurora@FleetBuzz on 2008-03-09
Thanks!

I removed the wrong driver and am downloading.

I see the notorious space is still in front of .inf.  Will remove for sure!

I'll let you know....

By the way, do I need to remove the blacklist entry I made earlier?

---

### Post by ghost_ryder35 on 2008-03-09
that space is really starting to get annoying too

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> that space is really starting to get annoying too

Ubuntu is telling me it can't open the file.  Do  I need to extract it somehow?
> donj@donj-laptop:~$ sudo ndiswrapper -i /home/donj/Desktop/174292.exe_files/DRIVER/bcmwl5.inf
[sudo] password for donj:
installing bcmwl5 ...
couldn't open /home/donj/Desktop/174292.exe_files/DRIVER/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
donj@donj-laptop:~$ 


---

### Post by Aurora@FleetBuzz on 2008-03-09
Sorry!  I answered my own question.  Just extracted and will try again....

---

### Post by Aurora@FleetBuzz on 2008-03-09
> donj@donj-laptop:~$ sudo ndiswrapper -i /home/donj/Desktop/174292.exe_files/DRIVER/bcmwl5.inf
installing bcmwl5 ...
couldn't open /home/donj/Desktop/174292.exe_files/DRIVER/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.:confused:
donj@donj-laptop:~$ 


:confused::(  Now this doesn't want to install....

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> :confused::(  Now this doesn't want to install....
make sure the path I specified is the path that it is located at.  eg the folder names are correct and there are no spaces or capitilization errors.

---

### Post by Aurora@FleetBuzz on 2008-03-09
I'm going through the GUI.  I opened the file and the driver, bcmwl5 is not listed!  This might be the problem.  bcmwl6 is listed.

---

### Post by ghost_ryder35 on 2008-03-09
use that one instead :)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> make sure the path I specified is the path that it is located at.  eg the folder names are correct and there are no spaces or capitilization errors.

Yes.  When I fixed that it told me it couldn't locate the driver.  When I opened **ndisgtk**, it showed **bcmwl5** to be invalid.  Sure enough, there's no driver I could find when I examined the contents of the directory I unzipped to my desktop....

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> I'm going through the GUI.  I opened the file and the driver, bcmwl5 is not listed!  This might be the problem.  bcmwl6 is listed.

did this one work?

---

### Post by Papa-san on 2008-03-09
It'd be under 'DRIVERS_US'

(BTW- the bcm43xx-fwcutter didn't work on mine, so I'm starting a thread on it.)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> use that one instead :)

No luck.
> donj@donj-laptop:~$ sudo ndiswrapper -i /home/donj/Desktop/Dell_multi_device_A17_R174292.exe_FILES/DRIVER/bcmwl6.inf
installing bcmwl6 ...
couldn't open /home/donj/Desktop/Dell_multi_device_A17_R174292.exe_FILES/DRIVER/bcmwl6.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
donj@donj-laptop:~$ 


---

### Post by ghost_ryder35 on 2008-03-09
> **Papa-san said:**
> It'd be under 'DRIVERS_US'

(BTW- the bcm43xx-fwcutter didn't work on mine, so I'm starting a thread on it.)

what about DRIVERS_US   is there a folder called that???? 
Aurora look for the file in that folder...

---

### Post by jan quark on 2008-03-09
try to remove the changes you have done until now
and try this guide

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **Papa-san said:**
> It'd be under 'DRIVERS_US'

(BTW- the bcm43xx-fwcutter didn't work on mine, so I'm starting a thread on it.)
That worked!

---

### Post by ghost_ryder35 on 2008-03-09
the driver works now????????????????????????????????????????

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> the driver works now????????????????????????????????????????
Alas, no.

I merely referred to the fact that I got it to install (which was a first by the way).

I rebooted and...nothing.

---

### Post by Aurora@FleetBuzz on 2008-03-09
Maybe this card is too new and there's no fix yet?  Might have to wait for the next release of Ubuntu?

---

### Post by ghost_ryder35 on 2008-03-09
what is the display when you do 
ndiswrapper -l

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> what is the display when you do 
ndiswrapper -l
Here it is:
> donj@donj-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4328) present
donj@donj-laptop:~$ 


(Ignore the smiley; I don't know how it got there....)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **jan quark said:**
> try to remove the changes you have done until now
and try this guide

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
Thank you for the link.  If all else fails.... :)

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> Here it is:

do this and then reboot

[B]sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules[/B]

---

### Post by ghost_ryder35 on 2008-03-09
if that does not work we will call it a day... but if it installed the driver and sees the hardware we should be good :)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> if that does not work we will call it a day... but if it installed the driver and sees the hardware we should be good :)
Note the last line "permission denied".  
> donj@donj-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4328) present
donj@donj-laptop:~$ sudo ndiswrapper -m
[sudo] password for donj:
module configuration already contains alias directive

donj@donj-laptop:~$ sudo modprobe ndiswrapper
donj@donj-laptop:~$ sudo echo ndiswrapper >> /etc/modules
bash: /etc/modules: Permission denied
donj@donj-laptop:~$ 

Haven't re-booted yet.  Will wait for your comment.

---

### Post by ghost_ryder35 on 2008-03-09
try this instead because of the permission error:
sudo -s
echo ndiswrapper >> /etc/modules
exit

---

### Post by Aurora@FleetBuzz on 2008-03-09
Did it.  Look OK?
> donj@donj-laptop:~$ sudo -s
root@donj-laptop:~# echo ndiswrapper >> /etc/modules
root@donj-laptop:~# exit
exit
donj@donj-laptop:~$ 


---

### Post by ghost_ryder35 on 2008-03-09
looks good.  Reboot and hopefully you will see it turn on :)

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> looks good.  Reboot and hopefully you will see it turn on :)
No, it did not turn on.  I tried FN+F2 to no avail.

Frankly, I'm at my wits end with this.

What do you suggest?  Wait for the next release of ubuntu?  Do a fresh install and try the route suggested by jan quark?  I don't know if that will work since it was for a different wireless card?

---

### Post by ghost_ryder35 on 2008-03-09
his route should work if you just change the file and folder names to the driver that you need....

---

### Post by Papa-san on 2008-03-09
even though it may be a different wireless card, the thing that is important (I think) is the chipset, and they use the same one of those on multiple cards.
 Starting from scratch is a BEAR, but it might be a good idea... That's what I am doing on my daughter's laptop right now...

---

### Post by Aurora@FleetBuzz on 2008-03-09
Any good guides on re-installing Ubuntu? 

I am dual booting on a single hard drive with vista.  I don't want to endanger vista!

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> Any good guides on re-installing Ubuntu? 

I am dual booting on a single hard drive with vista.  I don't want to endanger vista!

Youll be fine Ubuntu will just write over the existing Grub and will auto detect windows install

---

### Post by Aurora@FleetBuzz on 2008-03-09
Of course, the safe thing would be to just wait and see if Hardy Heron will have these drivers?  What do you think?

---

### Post by Papa-san on 2008-03-09
when you get to the partitioner, use manual, and DON'T do anything to any fat32 or NTSB partitions... just ext3 and ext2 for your swap.

What I can tell you is that you are learning a LOT doing what you are, even when it doesn't work... Don't be afraid to try it again... One simple problem early in the process could have had this messed up...

---

### Post by handydan918 on 2008-03-09
If I may butt-in...
Before we go nuclear here, could you post the output of ndiswrapper -l again?

---

### Post by Aurora@FleetBuzz on 2008-03-09
I'm going to just backtrack on this thread and "un-do" everything.  I really don't want to mess with bootloaders  and the like.

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **handydan918 said:**
> If I may butt-in...
Before we go nuclear here, could you post the output of ndiswrapper -l again?

Will do.  Let me get into the other OS!

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **handydan918 said:**
> If I may butt-in...
Before we go nuclear here, could you post the output of ndiswrapper -l again?
Here it is:

> bcmwl6 : driver installed
        device (14E4:4328) present
donj@donj-laptop:~$ 

---

### Post by handydan918 on 2008-03-09
Wonder what ```
iwlist scanning
``` would show you? 
I would suggest temoprarily disabling encryption, also.


The reason I posted the previous is because I fought and won this battle some time ago with a different bcm43xx chip. From memory, something like 
rmmod ndiswrapper
ndiswrapper -e (all drivers not being used)
ndiswrapper -l (to confirm driver present-hardware present)
ndiswrapper -m
modprobe ndiswrapper 

(all with appropriate sudo's inserted)
I found that the order of operations was critical to success, but it's been some months ago that I did this...
hope this helps.

---

### Post by Aurora@FleetBuzz on 2008-03-09
> donj@donj-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


What is completely confounding is that my wireless light is on!

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> What is completely confounding is that my wireless light is on!


damn.... eth1 would be your wireless interface, which isnt present so hmmm..... the wireless light is on which is good... maybe the interface is taking a while to boot?  Reboot possibly... What have you changed since the light was off?

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> damn.... eth1 would be your wireless interface, which isnt present so hmmm..... the wireless light is on which is good... maybe the interface is taking a while to boot?  Reboot possibly... What have you changed since the light was off?

I didn't change anything.  I was actually getting ready to do the re-install when I got a phone call!

However, the wireless icon at the top on the task pane still doesn't detect my router.

---

### Post by ghost_ryder35 on 2008-03-09
does it detect ANY routers?

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> does it detect ANY routers?
I just re-booted.  The wireless light is still there, but it is not picking up my router.  In other words, I have a blue wireless light showing on the front of my laptop, but the little computer icon which indicates connectivity shows that I'm not connected.  (i.e., the orange triangle with the exclamation point inside).  When I double click the icon, it opens a "network settings" dialogue box which shows "Wired connection" and "modem connection"; no "wireless connection".  

I think I might be close; at least the light is on.  Maybe the glass is almost half full....

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> I just re-booted.  The wireless light is still there, but it is not picking up my router.  In other words, I have a blue wireless light showing on the front of my laptop, but the little computer icon which indicates connectivity shows that I'm not connected.  (i.e., the orange triangle with the exclamation point inside).  When I double click the icon, it opens a "network settings" dialogue box which shows "Wired connection" and "modem connection"; no "wireless connection".  

I think I might be close; at least the light is on.  Maybe the glass is almost half full....
exactly, just left click once on the computer

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> exactly, just left click once on the computer
When I do that I get a box with "wired connection" greyed out.  When I open Manual configuration" no wireless connecting is showing.

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> When I do that I get a box with "wired connection" greyed out.  When I open Manual configuration" no wireless connecting is showing.

I'm still stumped, but the light is nice :)

---

### Post by Aurora@FleetBuzz on 2008-03-09
Any suggestion on how to "get the grey out"?:)

---

### Post by ghost_ryder35 on 2008-03-09
Can you go to System, Administration, Network and manually assign a IP address and such?

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **ghost_ryder35 said:**
> Can you go to System, Administration, Network and manually assign a IP address and such?

I'll try that.  Where do I get the info, such as IP address?

---

### Post by ghost_ryder35 on 2008-03-09
from your router, go to the windows machine and click start then type ipconfig /all, find your wireless card and copy the info down such as 

Ethernet adapter Local Area Connection:

        Description . . . . . . . . . . . : Intel(R) PRO/100 VM Network Connecti
on
        Physical Address. . . . . . . . . : 00-08-02-1E-B5-45
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.144.64.85
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.144.64.1
        DHCP Server . . . . . . . . . . . : 10.144.1.16
        DNS Servers . . . . . . . . . . . : 10.144.1.11
                                                          10.144.1.12
        Primary WINS Server . . . . . . . : 10.144.1.11
        Secondary WINS Server . . . . . . : 10.144.1.12
        Lease Obtained. . . . . . . . . . : Thursday, March 06, 2008 6:51:34 PM
        Lease Expires . . . . . . . . . . : Friday, March 14, 2008 6:51:34 PM

---

### Post by Aurora@FleetBuzz on 2008-03-09
Thanks.  I got the info and now I'll need to get back into Ubuntu and insert.  Where do I do this?  What do I do with the data?

---

### Post by Aurora@FleetBuzz on 2008-03-09
This is probably overkill, but here's the info from the Vista side of the house:
> Windows IP Configuration

   Host Name . . . . . . . . . . . . : donj-laptop
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : gt.rr.com

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : gt.rr.com
   Description . . . . . . . . . . . : Dell Wireless 1505 Draft 802.11n
 WLAN Min
i-Card
   Physical Address. . . . . . . . . : 00-1F-3A-3B-D6-09
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . :
 fe80::c566:4a0a:9666:62bf%10(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.103(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, March 09, 2008 12:50:04
 PM
   Lease Expires . . . . . . . . . . : Monday, March 10, 2008 12:50:04
 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 167780154
   DNS Servers . . . . . . . . . . . : 24.93.41.127
                                       24.93.41.128
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : gt.rr.com
   Description . . . . . . . . . . . : Marvell Yukon 88E8040 PCI-E Fast
 Ethernet
 Controller
   Physical Address. . . . . . . . . : 00-1D-09-44-E6-BD
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling
 Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . :
 2001:0:cf2e:308c:452:24e0:3f57:fe98(Prefe
rred)
   Link-local IPv6 Address . . . . . :
 fe80::452:24e0:3f57:fe98%8(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . : gt.rr.com
   Description . . . . . . . . . . . : isatap.gt.rr.com
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . :
 fe80::5efe:192.168.1.103%18(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 24.93.41.127
                                       24.93.41.128
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 10:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

---

### Post by zabien1970 on 2008-03-09
Just wondering if you right click on the internet triangle are both enable networking and enable wireless checked?

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **zabien1970 said:**
> Just wondering if you right click on the internet triangle are both enable networking and enable wireless checked?
No, they are not.  Only enable networking.  There is not option to enable wireless.

---

### Post by zabien1970 on 2008-03-09
Left click enable networking then see what happens

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **zabien1970 said:**
> Left click enable networking then see what happens
1.  On left click, "wired network" is greyed out; there is a "manual configureation" option, which opens up "Network Setting".  In "Network Settings" there is no "wired connection".
2.  On right click, there is a check by "Enable networking".  There is "connection information", but it is greyed out.

No wireless is recognized by ubuntu.  

The wireless light is lit on the computer.  It seems that the problem is that Ubuntu still doesn't recognize either the network  or the hardware.

---

### Post by Papa-san on 2008-03-09
Hey, I marked my thread on this problem as 'Solved'!

The mods are going to delete the thread, and I'm going to delete the Ubuntu partitions... Quite a solution, but it's all there is... I wish you luck!

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **Papa-san said:**
> 
The mods are going to delete the thread, and I'm going to delete the Ubuntu partitions... Quite a solution, but it's all there is... I wish you luck!

Thanks, but I'm just going to keep plugging away at this.  Worst case will be to wait for Hardy Heron; I can still update via ethernet.

BTW, you might want to use SuperGrub first and restore the Windows bootloader....

---

### Post by handydan918 on 2008-03-09
what does ```
sudo iwconfig
``` show you?

---

### Post by Aurora@FleetBuzz on 2008-03-09
iwconfig:
l> o        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Aurora@FleetBuzz on 2008-03-09
By the way, I realize that this thread is way too long, but I just wanted to thank everyone who took the time to try to help me out.   I think that Dell will probably sell a lot of Inspiron 1525s and a lot of these Broadcom cards.  It is definitely in the best interest of the community to figure this one out. 

I remain eternally optimistic....

---

### Post by ghost_ryder35 on 2008-03-09
> **Aurora@FleetBuzz said:**
> I remain eternally optimistic....
As do I.
Wish I had the same chipset as you so I could try multiple diffrent ways all day long...

---

### Post by handydan918 on 2008-03-09
Found a post where a guy claims to have this chipset working on 7.10...
It's [here]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4").

---

### Post by Aurora@FleetBuzz on 2008-03-09
> **handydan918 said:**
> Found a post where a guy claims to have this chipset working on 7.10...
It's [here]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4").

Thanks, handydan918.  I'll give it a shot later.  Before I do this, should I delete the driver's I've already installed, or will it matter?

Here's what I got from that link:
> wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
mkdir driver
unzip -a R151517.EXE -d driver/
cd driver/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
I've already installed Ndiswrapper and I know I have the same card/chip set.

---

### Post by handydan918 on 2008-03-09
> **Aurora@FleetBuzz said:**
> Thanks, handydan918.  I'll give it a shot later.  Before I do this, should I delete the driver's I've already installed, or will it matter?

Here's what I got from that link:

I've already installed Ndiswrapper and I know I have the same card/chip set.
I would be sure to go thru the steps exactly as the link says, including using the specified driver.

edit: 
well, any progress?

---

### Post by ghost_ryder35 on 2008-03-12
I'd love to get an update on this, let me know if you got it working....

---

### Post by Aurora@FleetBuzz on 2008-03-14
Sorry for the delay.  I was on a business trip and just recently got back.

Sorry to say that I have not been able to get it working.  I'm going to wait for Hardy Heron before I invest any more time.  Hopefully, the driver will be part of the new release.

Thanks again for all your help, and the help of all the others here who worked with me to get this thing working.

---

