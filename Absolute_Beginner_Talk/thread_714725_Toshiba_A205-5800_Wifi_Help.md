---
title: "Toshiba A205-5800 Wifi Help"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by steven.robles on 2008-03-04
Hello,
     I was wondering if anyone has found a wifi fix for the Toshiba A205-5800.  Everything seems to be working fine, minus the wifi.  If anyone has any input, I appreciate your advice.  Thanks.

New to Ubuntu,
Steve

---

### Post by Crooksey on 2008-03-04
Can you paste the results of...

```

$ iwconfig
```

---

### Post by jan quark on 2008-03-04
and also the result of
```

sudo lshw -C network
```
```

cat /etc/network/interfaces
```
```

sudo iwlist scan
```

---

### Post by steven.robles on 2008-03-05
senorpenguino@senorpenguino-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

senorpenguino@senorpenguino-laptop:~$ sudo lshw -C network
[sudo] password for senorpenguino:
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:9b:16:94
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

senorpenguino@senorpenguino-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

senorpenguino@senorpenguino-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


Thank you for your time,
Steve

---

### Post by anewguy on 2008-03-05
Please also post back the following from a terminal window:

lspci


This will list the PCI devices and hopefully show the maker/model of the chipset for your wireless - from there we can look for drivers.

:)

---

### Post by steven.robles on 2008-03-05
senorpenguino@senorpenguino-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

---

### Post by anewguy on 2008-03-05
I looked at Toshiba's site for your model and they show only 1 wireless driver that would work with Windows XP SP2.  This may be able to be used using ndiswrapper, but first we need to know if you have 32-bit or 64-bit Ubuntu installed.

We can give detailed instructions for using ndiswrapper with the XP drivers if you are using 32-bit.  First, download the driver from the link below, then extract the .sys and .inf files to your desktop.  From the looks of things, there are 3 different combinations, so it may take a couple of tries with ndiswrapper to get it working.

[http:/http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=1816234&moid=1905971&rpn=PSAF3U&BV_SessionID=@@@@1115026344.1204704106@@@@&BV_EngineID=ccccadedhjmmfedcgfkceghdgngdgnn.0&ct=DL&all_docs=false/]("http:/http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=1816234&moid=1905971&rpn=PSAF3U&BV_SessionID=@@@@1115026344.1204704106@@@@&BV_EngineID=ccccadedhjmmfedcgfkceghdgngdgnn.0&ct=DL&all_docs=false/")

After you have downloaded an extracted the .inf and .sys files, post back and we'll go from there.  It may be a while as it is very late here so I won't be back on until Tuesday late afternoon or evening US central time.

:)

---

### Post by steven.robles on 2008-03-06
Ok, I downloaded that driver to my desktop and extracted the folder from the .exe file.  There are a bunch of .inf and .sys files in there.  Which ones should I be extracting to my desktop?  

They are:

NETw4k32.inf
NETw4k32.sys
NETw4x32.inf
NETw4x32.sys
NETw4x64.inf
NETw4x64.sys
w29n50.sys
w29n51.inf
w29n51.sys

I am using 32-Bit Ubuntu

Thanks

---

### Post by anewguy on 2008-03-06
Okay, glad you got that.  I mentioned there seemed to be multiple drivers since I hadn't seen that before.  Since you are running 32-bit, we can rule out the 64-bit files, but that still leaves us with 6 files (3 probable drivers?).  We can try these starting with the first and see what happens.

First thing you need to do now is start up synaptic package manager and search for ndis*.  If ndiswrapper and/or the utilities are not green boxed, check the box then apply.  This way we can be sure you have ndiswrapper installed.

Now, we need to go to a terminal window:

applications/accessories/terminal

now type the following (each followed by enter)

cd ~/Desktop

sudo ndiswrapper -i NETw4k32.inf  (that's a lower case "I" for "Install")

sudo ndiswrapper -l (lower case "L" for "List")

your device and driver should show as installed with no errors.  If there are errors, copy the screen and paste back here so we can start again.

Assuming no errors:

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

While the "sudo ndiswrapper -m" supposedly sets up the module for loading, it seems sometimes that is not the case.  To be save, we also need to add ndiswrapper to the kernel modules list to be loaded at boot:

cd /etc

sudo gedit modules

add the following line to the end of that file:

ndiswrapper

save the file, exit, and then REBOOT.

When the boot comes back up, check you networking icon to see if the wireless networks are listed.

Please post back your results.

:)

---

### Post by steven.robles on 2008-03-06
senorpenguino@senorpenguino-laptop:~$ cd ~/Desktop
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -i NETw4k32.inf
[sudo] password for senorpenguino:
installing netw4k32 ...
couldn't open NETw4k32.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -l
netw4k32 : invalid driver!
senorpenguino@senorpenguino-laptop:~/Desktop$ 

invalid driver error,

---

### Post by anewguy on 2008-03-06
Okay, the first thing we need to do is clear the driver from ndiswrapper:

sudo ndiswrapper -e netw4k32

sudo ndiswrapper -l (lower case "L"). If anything is returned please post it back here.

Now on to trying to load the driver again.  Once you are in a terminal window again:

cd ~/Desktop

ls

Post the result back here, as it appears the file name may be slightly different.  I'm curious as to why even when the capital letters are specified it still looks like ndiswrapper is seeing lower case.

After you post the output back, we can go from there.

:)

---

### Post by stchman on 2008-03-06
> **steven.robles said:**
> Hello,
     I was wondering if anyone has found a wifi fix for the Toshiba A205-5800.  Everything seems to be working fine, minus the wifi.  If anyone has any input, I appreciate your advice.  Thanks.

New to Ubuntu,
Steve

From what you have posted, it looks like your laptop does not have a built in wireless card.

According to Toshiba's website your laptop is supposed to have a Realtek 802.11b/g wireless card.

---

### Post by mrnuke7571 on 2008-03-06
I get the same results as the original poster on my new Toshiba A205-S5800 laptop.
With windows Vista wireless worked fine, so I know it has a wireless card built-in. Supposedly the Realtek 802.11b/g one, but can't find the exact specs of it. :confused:

Here are the drivers I found for this model, but nothing with realtec WiFI?
[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?BV_SessionID=%40%40%40%400394796667.1204846909%40%40%40%40&BV_EngineID=cccgadedhjmmidecgfkceghdgngdgmn.0&ModelDLOS=null&ModelDLCat=null&BV_SessionID=%40%40%40%400394796667.1204846909%40%40%40%40&BV_EngineID=cccgadedhjmmidecgfkceghdgngdgmn.0&ListType=Model&ct=DL&moid=1905971&rpn=PSAF3U&OrderBy=D&PublicStartIndex=0&PrivateStartIndex=0&PublicCutOff=&PrivateCutOff=&AddOldPublicItems=false&AddOldPrivateItems=undefined&all_docs=false#PublicList](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?BV_SessionID=%40%40%40%400394796667.1204846909%40%40%40%40&BV_EngineID=cccgadedhjmmidecgfkceghdgngdgmn.0&ModelDLOS=null&ModelDLCat=null&BV_SessionID=%40%40%40%400394796667.1204846909%40%40%40%40&BV_EngineID=cccgadedhjmmidecgfkceghdgngdgmn.0&ListType=Model&ct=DL&moid=1905971&rpn=PSAF3U&OrderBy=D&PublicStartIndex=0&PrivateStartIndex=0&PublicCutOff=&PrivateCutOff=&AddOldPublicItems=false&AddOldPrivateItems=undefined&all_docs=false#PublicList)

I just got off the phone with Toshiba, and after me explaining it to a few techs what I was looking for, one FINALLY grasped the idea of why I don't want to use Device manager in Windowze to get the driver specs.

It supposedly is a : Wireless intel wireless wifi link 4965agn card.
NOT a Realtek.

---

### Post by mrnuke7571 on 2008-03-06
Ahh it continues....:lolflag:

I checked the Device Manager and it is listing the wireless device as an RTL8187B.

---

### Post by anewguy on 2008-03-07
Either way around, the link I provided is for the only wifi driver listed on Toshiba's site for that specific model, so we should be okay working with it. :)

---

### Post by steven.robles on 2008-03-07
Wow, i was just wondering why I wasn't receiving any more responses from my posts... then I found the "Page 2" Button :lolflag: sigh...

Im doing that stuff right now, ill repost in a few mins...

---

### Post by steven.robles on 2008-03-07
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4k32
[sudo] password for senorpenguino:
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4k32
couldn't delete /etc/ndiswrapper/netw4k32: No such file or directory
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -l
senorpenguino@senorpenguino-laptop:~$ cd ~/Desktop
senorpenguino@senorpenguino-laptop:~/Desktop$ ls
driver_wifi_intel_os2007223a.exe  driver_wifi_intel_os2007223a.exe_FILES
senorpenguino@senorpenguino-laptop:~/Desktop$

---

### Post by anewguy on 2008-03-08
Well, the ls (list) of your desktop folder only shows the .exe files.  You need to extract the 6 .inf and .sys files from them and place those files on your desktop.  Then do another ls again - if the individual files shows, try the instructions again, matching the file name (case and spelling) to that which shows on the ls.

:)

---

### Post by steven.robles on 2008-03-08
so, i need to put all .inf and .sys files from that folder to my desktop?

---

### Post by anewguy on 2008-03-08
Yes.  The 2 .exe's are the Windows driver installation files.  You need extract just the .inf and .sys files from that and place the .inf and .sys files on your desktop.

You can probably open the .exe by just clicking on it - it will probably open in a "unpacker" windows (I can't right now remember the name).  Go through that on the screen until you find the .sys and .inf files (a lot of times they are in a subfolder called drivers).  Highlight and extract each of those to your desktop.

:)

---

### Post by steven.robles on 2008-03-08
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4k32
[sudo] password for senorpenguino:
couldn't delete /etc/ndiswrapper/netw4k32: No such file or directory
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -l
senorpenguino@senorpenguino-laptop:~$ cd ~/Desktop
senorpenguino@senorpenguino-laptop:~/Desktop$ ls
driver_wifi_intel_os2007223a.exe        NETw4k32.sys  NETw4x64.INF  w29n51.inf
driver_wifi_intel_os2007223a.exe_FILES  NETw4x32.INF  NETw4x64.sys  w29n51.sys
NETw4k32.INF                            NETw4x32.sys  w29n50.sys
senorpenguino@senorpenguino-laptop:~/Desktop$

---

### Post by anewguy on 2008-03-08
Okay, you should be able to follow my previous installation instructions (the long post) now.  Since I don't know which of the drivers it actually wants, let's start with the first, so you want to start the process using the NETw4x32.INF file with ndiswrapper.  Remember to match the case and spelling exactly:

sudo ndiswrapper -i NETw4x32.INF 

sudo ndiswrapper -l


Post those results back and we'll go from there.  Note I haven't finished the installation here, just trying to see if it will load and recognize this particular driver.

:)

---

### Post by anewguy on 2008-03-08
BTW - although it's 1:27 in the morning here, I'll be up for a while so I'll keep checking back to see if you've replied.  May be a few minutes between your post and my reply.  :)

---

### Post by steven.robles on 2008-03-08
I will also be on for a while =) No work tomorrow :guitar: Here's the results from that first one:

senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -i NETw4x32.INF
[sudo] password for senorpenguino:
installing netw4x32 ...
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -l
netw4x32 : driver installed
senorpenguino@senorpenguino-laptop:~/Desktop$

---

### Post by steven.robles on 2008-03-08
And this was after I did everything you mentioned in that long post:
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -i NETw4x32.INF
[sudo] password for senorpenguino:
installing netw4x32 ...
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -l
netw4x32 : driver installed
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo depmod -a
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo modprobe ndiswrapper
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
senorpenguino@senorpenguino-laptop:~/Desktop$ cd /etc
senorpenguino@senorpenguino-laptop:/etc$ sudo gedit modules

I also added ndiswrapper to the end of that file.  Saved, and Rebooting now...

---

### Post by anewguy on 2008-03-08
Any luck yet?  If not, I would use sudo ndiswrapper -l so you can see the exact name/spelling, then do sudo ndiswrapper -e with that name.  Next I would try this driver:

w29n51.inf

:)

---

### Post by steven.robles on 2008-03-08
This is what I got after installing w29n51.inf:

senorpenguino@senorpenguino-laptop:~$ cd ~/Desktop
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -i w29n51.inf
installing w29n51 ...
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -l
w29n51 : driver installed
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo depmod -a
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo modprobe ndiswrapper
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -m
module configuration already contains alias directive

What should I be looking for after installing these drivers?  How do I know we were successful?

---

### Post by anewguy on 2008-03-08
If you installed regular Ubuntu, there is a network icon on the top bar, usually towards the right side. Click on this icon and see if any wireless networks show.  :)

---

### Post by steven.robles on 2008-03-08
I tried to install everything that ended in either .inf or .sys and the only 2 that actually installed were NETw4x32.INF and w29n51.inf.  Everything else was either for the 64-bit or after the "sudo ndiswrapper -l" they came up with invalid driver.  Did I do something wrong?

---

### Post by anewguy on 2008-03-08
If this got things working, please use the "Thread" clickable at the top of the post and mark it as "Solved" so it can help others.  If not, post back and we'll keep working on it.  :)

---

### Post by anewguy on 2008-03-08
I don't think you did anything wrong - I suspect it will only take 1 of those drivers, so if it took one try looking in the network icon and see if wireless networks show there.  You may also need to go networks (I'm running KDE, but I think in Gnome it's something like System/Administration/Network) and look at the wireless tab and be sure that roaming is enabled.

:)

---

### Post by steven.robles on 2008-03-08
Still nothing, The only 2 things it says when I bring up Network is "Wired Connection - Roaming Enabled" and "Modem Connection - This Network Interface is not connected"  Also in the Network window, there is no "Wireless" tab.  The only tabs that are there are "Connections" "General" "DNS" "Hosts"

---

### Post by anewguy on 2008-03-08
Try the following from someone's earlier post to see if the output has changed now:


Code:

sudo lshw -C network

Code:

cat /etc/network/interfaces

Code:

sudo iwlist scan

Also, try:

iwconfig


Post the output from those back here and we'll try again.  :)

---

### Post by steven.robles on 2008-03-08
senorpenguino@senorpenguino-laptop:~$ 
senorpenguino@senorpenguino-laptop:~$ sudo lshw -C network
[sudo] password for senorpenguino:
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:9b:16:94
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmw

senorpenguino@senorpenguino-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.are=N/A ip=192.168.1.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

senorpenguino@senorpenguino-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

senorpenguino@senorpenguino-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

senorpenguino@senorpenguino-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by anewguy on 2008-03-08
Hummmm......it still doesn't know about your wireless device (should be showing as eth1 I think).  So, I'll ask a copuple of questions here and then I'm heading off to bed for the night:

Obviously the "64" drivers won't work, as they are for 64-bit os.  However, with each of the other .inf files (3 total besides the "64", right?), did you first remove any existing driver from ndiswrapper 1st via ndiswrapper -e drivername  ?  You need a clean slate each time you start with ndiswrapper.

Do you also have Windows installed?  If so, can you look in device manager for your wireless and see if it says the type?

I'll keep looking and thinking - there should be some way to get it work! :)

---

### Post by anewguy on 2008-03-08
Hey Steve:  based on a post ealier in this thread where someone mentioned the wireless adapter should be intel 4965 xxx, I found this how-to you may want to try.  If you have questions about it, feel free to post back.  Sorry I didn't find it earlier!!!  Looks like it works without ndiswrapper, so be sure to follow the section about "if you have ndiswrapper running".

:)

---

### Post by steven.robles on 2008-03-08
Doh, didn't know I had to start with a clean slate each time.  I'll use the command you gave me and start from scratch.  

Yes, I also have Vista installed, I'll post what device manager says before I head to bed

Thanks again for your patience, gnight!

---

### Post by steven.robles on 2008-03-08
Under Device Manager, it shows my wireless card as Realtek RTL8187B Wireless 802.11g 54 Mbps USB 2.0 Network Adapter.

I haven't seen anything Intel...

---

### Post by steven.robles on 2008-03-08
Where was that "How-to" located you referred to for the intel 4965 xxx?

---

### Post by anewguy on 2008-03-08
Well, since your card is Realtek, I don't think the intel page would apply.  I did a search and found some other posts on your card - one of those posts is:

[http://ubuntuforums.org/showthread.php?t=571046]("http://ubuntuforums.org/showthread.php?t=571046")

You'll need to read the entire thing first before starting.  I also found by looking at that post and some others that the reason your internal wireless doesn't show on any of the list commands is that it is actually a USB device.  If you go into a terminal window and type "lsusb"  you'll probably get a long list, and included in that you will see your Realtek wireless.  Please post the output of that back here.

This is pretty new ground for me - I have no trouble with ndiswrapper, but it looks like there are some specific things (like compiling the driver, kernel module, etc.) that I haven't done before.  I will be glad to do my best and try to help you with this!  :)

---

### Post by anewguy on 2008-03-08
I also just found the Realtek drivers themselves.  I would do the following:

sudo ndiswrapper -l

using

sudo ndiswrapper -e xxxxxx

remove any drivers listed 

On your desktop, delete the .exe, .inf and .sys files from the drivers I had you download from Toshiba.

Go to this link, and let's try the WindowsME driver 1st:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#351]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#351")


You will need to extract the relevant driver files again from that download and place them on your desktop, then try the instructions again.  I think these may also require a macxxxx module to be loaded from what I read elsewhere - I'll try to find that.

The result of ndiswrapper -l when done should show both the driver and the device enabled.

Realtek also has a Linux driver on that site - I have no experience with any of the Realtek stuff, so this will be new ground for me as well!

:)

---

### Post by steven.robles on 2008-03-09
senorpenguino@senorpenguino-laptop:~$ lsusb
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
senorpenguino@senorpenguino-laptop:~$ 

Okay, there's the results from lsusb.  I'm going to take a look at that thread you posted.  Thanks again. (BTW I'll be on for a while again tonight).

---

### Post by steven.robles on 2008-03-09
senorpenguino@senorpenguino-laptop:~$ lsusb
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -l
[sudo] password for senorpenguino:
netw4k32 : invalid driver!
netw4k32.sys : invalid driver!
netw4x32.sys : invalid driver!
w29n51 : driver installed
senorpenguino@senorpenguino-laptop:~$ using
bash: using: command not found
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4k32
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4k32.sys
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4x32.sys
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e w2951
couldn't delete /etc/ndiswrapper/w2951: No such file or directory
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e w29n51
senorpenguino@senorpenguino-laptop:~$ 

okay, I think I removed them all successfully, I will now download the WinME drivers.  After I extract them to the desktop, will I be doing the same thing I was before (of course uninstalling the previous driver before installing the next one)?

---

### Post by anewguy on 2008-03-09
You may need to modprobe another kernel module - something that starts with mac, but right now I'd have to go looking again to find it.  I'll wait until you've tried the ME driver and we'll see how that goes (someone in one of the posts recommended the Win98 driver, but none of the "go"s for downloading for Win98, XP or Vista were available when I looked, that's why I suggested the ME driver.

Usually wireless is just a little work to get installed - I suspect that my unfamiliarity with your Realtek is making things slower than they might need be, but I'm doing my best!  :)

---

### Post by steven.robles on 2008-03-09
I appreciate all your help with this, I would be COMPLETELY lost if it weren't for your help.  Well, I'm still reading up on this stuff and I'm just about to install the WinME driver, wish me luck! Ill post results asap.:)

---

### Post by steven.robles on 2008-03-09
No luck with the WinME drivers

senorpenguino@senorpenguino-laptop:~$ lsusb
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -l
[sudo] password for senorpenguino:
netw4k32 : invalid driver!
netw4k32.sys : invalid driver!
netw4x32.sys : invalid driver!
w29n51 : driver installed
senorpenguino@senorpenguino-laptop:~$ using
bash: using: command not found
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4k32
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4k32.sys
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e netw4x32.sys
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e w2951
couldn't delete /etc/ndiswrapper/w2951: No such file or directory
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -e w29n51
senorpenguino@senorpenguino-laptop:~$ sudo ndiswrapper -l
senorpenguino@senorpenguino-laptop:~$ cd ~/Desktop
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -i net8187b.inf
[sudo] password for senorpenguino:
installing net8187b ...
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -l
net8187b : driver installed
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo depmod -a
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo modprobe ndiswrapper
senorpenguino@senorpenguino-laptop:~/Desktop$ sudo ndiswrapper -m
module configuration already contains alias directive

senorpenguino@senorpenguino-laptop:~/Desktop$ 

Installed, rebooted, no luck.  I uninstalled everything again, and I finished reading that other thread.  There seemed to be a lot of works for some but not for others.  A lot of it (especially the commands) was pretty tough for me as well, but I'm learning:)  What next?

---

### Post by anewguy on 2008-03-09
Well, I guess you'll need to try to follow that thread.  Read it entirely first, as there are little things here and there, and there is also a download of a patched driver mentioned.  Before you start that, you'll want to edit /etc/modules again and remove ndiswrapper from there.

Let me know if you have some questions along the way with that thread and I'll see if I can answer them for you.

:)

---

### Post by ercork on 2008-04-06
post_erasmus posted the solution on page 11 of 

[http://ubuntuforums.org/showthread.php?t=571046&highlight=toshiba+a205+wireless](http://ubuntuforums.org/showthread.php?t=571046&highlight=toshiba+a205+wireless)

Basically you have to edit the win98 driver as instructed. Then see my post on page 12 for the remaining bits.

---

