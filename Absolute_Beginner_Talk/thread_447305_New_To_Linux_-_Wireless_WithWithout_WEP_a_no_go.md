---
title: "New To Linux - Wireless With/Without WEP a no go"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by mwm1 on 2007-05-17
I am completly new to Linux, as in I installed it for the first time yesterday and am having a lot of problems with my wireless connection.  I'm trying to get this working on Ubuntu 7.04.

Card: D-Link DWL-G122 rev. C1 (USB)
Chipset: Ralink RT73 (RT2571W)

So I have WEP set up with a 64bit hex key and when booting into Ubuntu I can see my network - no problem there.
I punch in my WEP key and it never connects.  I tried both open/shared through Ubuntu and also through the Linksys router.
I googled this problem and was messeing around with commenting out some stuff from a network file then creating some sort of wpa file in the /etc/default/network folder I believe but nothing worked.

I scrapped the WEP and tried with no security and was able to connect but with 0% signal strength - also, I get no IP address and everything else is 0'd out.

I ran some command and got the following:

```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.462 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:41:7F:91:A6   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've also included a snapshot I took of another spot in Linux.

[[IMG]http://img508.imageshack.us/img508/9423/screenshotyk9.th.png[/IMG]](http://img508.imageshack.us/my.php?image=screenshotyk9.png)

IDK what of the above is relevant but I thought I would include anything i could think of.

Any help would be appreciated - please keep in mind yesterday was the first time I have ever used the terminal.:)

---

### Post by Bachstelze on 2007-05-17
```
sudo iwconfig wlan0 essid YOUR_ESSID key YOUR_WEP_KEY
sudo dhclient wlan0
```

you're there.

---

### Post by trent dillman on 2007-05-17
...

---

### Post by mwm1 on 2007-05-17
> **HymnToLife said:**
> ```
sudo iwconfig wlan0 essid YOUR_ESSID key YOUR_WEP_KEY
sudo dhclient wlan0
```

you're there.

Here's what happened when I ran the above.

```

sudo iwconfig wlan0 essid home key my_key_was_here
medeiros@medeiros-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:15:e9:a5:13:70
Sending on   LPF/wlan0/00:15:e9:a5:13:70
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

and here is my network file contents
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by Bachstelze on 2007-05-17
Your wifi card couldn't find any DHCP servers. Maybe you mistyped your ESSID and/or your key, or your network is not running DHCP.

---

### Post by mwm1 on 2007-05-17
> **HymnToLife said:**
> Your wifi card couldn't find any DHCP servers. Maybe you mistyped your ESSID and/or your key, or your network is not running DHCP.

It all runs fine in Win XP - it's a cable connection using DHCP.
I am certain I typed the ESSID and key correctly, proper case and all.

[[IMG]http://img247.imageshack.us/img247/5547/screenshot1hw5.th.png[/IMG]](http://img247.imageshack.us/my.php?image=screenshot1hw5.png)

---

### Post by mwm1 on 2007-05-17
> **trent dillman said:**
> I have an RT73 based wifi, working :-)

Uninstall network-manager and avahi-autoipd.

Install [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

I don't know how to do any of those things...:(

---

### Post by trent dillman on 2007-05-18
...

---

### Post by mwm1 on 2007-05-18
OK, I started the steps above then got stuck.

```

medeiros@medeiros-desktop:~$ sudo apt-get remove avahi-autoipd network-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avahi-autoipd network-manager network-manager-gnome ubuntu-desktop
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 2560kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88001 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing avahi-autoipd ...
Missing interface name.
Removing network-manager-gnome ...
Removing network-manager ...
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
medeiros@medeiros-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 07d1:3c03 D-Link System 
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
medeiros@medeiros-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
medeiros@medeiros-desktop:~$ 

```

Also, wouldn't the following step a few lines down require internet access or am I way off base:
```

sudo wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz

```

---

### Post by mwm1 on 2007-05-18
.

---

### Post by ugm6hr on 2007-05-18
I think you are right - you can't apt-get without internet access.  And the wget command also needs an active connection.  Can't guarantee this will work, but...

build-essential can be manually downloaded from:
[http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential) (just click on the link under the appropriate architecture, then pick a mirror).  When you have downloaded this, transfer it to the Ubuntu computer without internet, and just open it (double-click).  This will open GDebi, which will warn you about manually doing this, and then either complete the install, or tell you what other components you need before that's possible.  Unfortunately, it's then a case of searching for all the other necessary components - but they will all be in the [http://packages.ubuntu.com/feisty](http://packages.ubuntu.com/feisty) area for similar download.

As for the wget tar - presumably you can do the same.  I believe you can download it from the location given, then transfer to Ubuntu computer and just "Start Terminal here" in the directory you've copied it to, and type the same command in the terminal.

Unfortunately, I'm a relative beginner too, so apologies if I'm totally wrong.

---

### Post by mwm1 on 2007-05-18
Anything helps.

I'll give it a try and report back.

---

### Post by n8bounds on 2007-05-18
The build-essential is mostly a package that has nothing useful in it but requires other (useful) packages.  You may want to DL all the dependancies of that package as well.  Is there no place on earth you can quickly get at an ethernet cable to do this part?  Would save you a lot of headache...

---

### Post by mwm1 on 2007-05-18
> **n8bounds said:**
> The build-essential is mostly a package that has nothing useful in it but requires other (useful) packages.  You may want to DL all the dependancies of that package as well.  Is there no place on earth you can quickly get at an ethernet cable to do this part?  Would save you a lot of headache...

I hate wireless but the modem and cable hookup is 2 floors down and i'm on a desktop PC so I gotta take the scenic route :)

I think i've almost gotten the build essential thing installed...

---

### Post by mwm1 on 2007-05-18
I am stuck now with a file dependency.

2 different items are asking for g++-4.1

[http://packages.ubuntu.com/feisty/devel/g++-4.1](http://packages.ubuntu.com/feisty/devel/g++-4.1)

I select to download it and I get something called g++-4.1_4.1.2-0ubuntu4_i386.deb which doesn't do the trick.

[[IMG]http://img508.imageshack.us/img508/7296/71567007aw7.th.png[/IMG]](http://img508.imageshack.us/my.php?image=71567007aw7.png) & [[IMG]http://img508.imageshack.us/img508/7606/34532929yc8.th.png[/IMG]](http://img508.imageshack.us/my.php?image=34532929yc8.png)

---

### Post by ugm6hr on 2007-05-19
Does g++-4.1_4.1.2-0ubuntu4_i386.deb install OK?  It might be worth re-installing it (or redownloading and re-installing), just in case it got corrupted during the scenic route download...  I'm pleased that my advice has got you some way towards the destination!

---

### Post by mwm1 on 2007-05-19
> **ugm6hr said:**
> Does g++-4.1_4.1.2-0ubuntu4_i386.deb install OK?  It might be worth re-installing it (or redownloading and re-installing), just in case it got corrupted during the scenic route download...  I'm pleased that my advice has got you some way towards the destination!

No - when I try and install _g++-4.1_4.1.2-0ubuntu4_i386.deb_ it asks for_ libstdc++6-4.1-dev_ which in turn asks for _g++-4.1_ and then I'm back to where I started. :(

---

### Post by ugm6hr on 2007-05-19
Hmmm... 

I've had a similar problem trying to manually download Network Manager.  Essentially some dependencies work in 2 directions (or in a circle in your example).  I think it is theoretically possible to do the install via Synaptic Package Manager with files from a CD rather than internet (it seems to give this option), but I have no idea whether it will work, since I managed to connect without Network Manager, and downloaded it.

Anyway - here's what I was going to do if I had to:
1. Open Synaptic Package Manager
2. Settings -> Repositories
3. In "Third Party Software" tab
 3b. if files on CD -> add CD-ROM

From there it would be guesswork I'm afraid.  

It looks like it allows you to add directories with the "Add...", but I have no idea what the syntax is for that.  I did find where the list is kept (/etc/apt/sources.list), and it looks like it should be something like "deb location main", but I suspect it won't be nearly that easy!  Might be worth looking at how it is done on the Live CD, cos I know you are supposed to be able to install from Synaptic using that.

PS: Please try not to make a mess of your installation following my complete lack of knowledge.

---

### Post by mwm1 on 2007-05-19
Good news, I was able to get through all the instructions provided by trent.
Bad news, it still doesn't work.

Not everything was as smooth as i had hoped and in a few spots I made judgement calls which were probabley incorrect.

My wireless USB NIC is a D-Link but when I pulled it up in the hardware tool it was listed as Ralink
[[IMG]http://img185.imageshack.us/img185/521/screenshotdevicemanagerfo0.th.png[/IMG]](http://img185.imageshack.us/my.php?image=screenshotdevicemanagerfo0.png)

So when I got to the portion of instructions on adding my info to the file rtmp_def.h I decided to just change the name on the first listing of D-Link because the first set of numbers matched up with the device.
[[IMG]http://img185.imageshack.us/img185/277/screenshotsdesktopmediasz0.th.png[/IMG]](http://img185.imageshack.us/my.php?image=screenshotsdesktopmediasz0.png)
but when I do the lsusb thing the device shows as D-Link so IDK which is right.


rc.local
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

dhclient3 rausb0
exit 0

```

network interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface rausb0 inet dhcp
wireless-essid home

#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```


sudo ifconfig rausb0 down
sudo ifconfig rausb0 up
sudo iwconfig rausb0 essid your_essid
sudo dhclient3 rausb0
```

medeiros@medeiros-desktop:~$ sudo ifconfig rausb0 down
rausb0: ERROR while getting interface flags: No such device
medeiros@medeiros-desktop:~$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device
medeiros@medeiros-desktop:~$ sudo ifconfig rausb0 essid home
essid: Unknown host
ifconfig: `--help' gives usage information.
medeiros@medeiros-desktop:~$ sudo dhclient3 rausb0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
rausb0: ERROR while getting interface flags: No such device
rausb0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

I think I most likely took a wrong turn somewhere...

---

### Post by Bachstelze on 2007-05-19
The reason you see it as Ralink is that while your adapter is D-Link, it has a Ralink chipset in it (think of it the same way as an Asus graphics card with w nvidia chipset, for example).

No such device for rausb0, that's weird...

```
sudo iwconfig
```

What gives ?

---

### Post by mwm1 on 2007-05-20
```

sudo iwconfig

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

I also tried renaming the Ralink back to D-Link in rtmp_def.h but nothing has changed.

---

### Post by Bachstelze on 2007-05-20
Then replace rausb0 with wlan1 in those intructions you were given.

---

### Post by RKCole on 2007-05-20
I wish taht I woudl have caught this post earlier.  I purchased a Wireless-G USB Dongle awhile ago that uses the RaLink RT73 chipset.  I was uanble to get anything working, but after a lot of research I now have mine up and running with WPA2-PSK+TKIP.  It also works with AES encryption.  I wrote a guide on it which worked for some other users; if you'd like, private message me and I can e-mail it to you.  The guide, unfortuantely, is about 40KB over the forum size limit.

If I can be fo any help, pleae let meknow.

Take care.

---

### Post by mwm1 on 2007-05-20
> **HymnToLife said:**
> Then replace rausb0 with wlan1 in those intructions you were given.

I did the above and now have something a lot more promising

```

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Still no connection yet.

---

### Post by Bachstelze on 2007-05-20
You must specify the ESSID of the network you want to connect to, and the WEP key if it uses one :

```
sudo iwconfig eth1 essid YOUR_ESSID key YOUR_EP_KEY
```

Then run dhclient again (if you want to connect with DHCP).

---

### Post by mwm1 on 2007-05-20
Wow I think I am right on the brink of having this work! :D

```

medeiros@medeiros-desktop:~$ sudo iwconfig wlan1 essid home key CE2960D365
medeiros@medeiros-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"home"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:CE29-60D3-65
          Link Quality=0/100  Signal level:-84 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

medeiros@medeiros-desktop:~$ sudo dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 5124
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:15:e9:a5:13:70
Sending on   LPF/wlan1/00:15:e9:a5:13:70
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
medeiros@medeiros-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"home"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0C:41:7F:91:A6   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:CE29-60D3-65
          Link Quality=67/100  Signal level:-70 dBm  Noise level:-107 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Shows link quality along w/ my network name and key but still no connection.

---

### Post by trent dillman on 2007-05-20
...

---

### Post by mwm1 on 2007-05-20
```

medeiros@medeiros-desktop:~$ sudo iwconfig wlan1 essid home key CE2960D365
medeiros@medeiros-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"home"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0C:41:7F:91:A6   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:CE29-60D3-65
          Link Quality=73/100  Signal level:-64 dBm  Noise level:-107 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

medeiros@medeiros-desktop:~$ sudo iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 00:0C:41:7F:91:A6
                    ESSID:"home"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

```

---

### Post by trent dillman on 2007-05-20
...

---

### Post by Bachstelze on 2007-05-20
> **trent dillman said:**
> hmm...

what about ```
lsmod | grep rt73
```?

What for ? If the interface appears, that means the module is loaded...

---

### Post by mwm1 on 2007-05-20
```

medeiros@medeiros-desktop:~$ sudo lsmod | grep rt73
rt73               214528  0 
usbcore            134280  6 rt2570,rt73,usbhid,ehci_hcd,ohci_hcd

```

---

### Post by mwm1 on 2007-05-21
Anybody got any new ideas?

I don't understand how it could be connected and doing everything but sending/receiving.

---

### Post by Austin_KW on 2007-05-21
You have two ralink drivers loaded; rt73 & the older chipset rt2570
you may also have rt73usb loaded but it is not shown in above post.

you need to "gksudo gedit /etc/modprobe.d/blacklist" and add the following lines to stop these drivers from loading
```

# Blacklist some ralink drivers; will use rt73
blacklist rt73usb
blacklist rt2570
```
then reboot

---

### Post by mwm1 on 2007-05-21
Holy crap it's working now!

Final thing, is there a way to set this up to pre populate my essid and WEP key so I don't need to enter the terminal every time i want to connect?

---

### Post by Austin_KW on 2007-05-21
Yes "gksudo gedit /etc/network/interfaces"
and add the following lines to auto configure wlan1 (assuming your interface is still wlan1)

```

auto wlan1
iface wlan1 inet dhcp
	pre-up ifconfig wlan1 up
	pre-up iwconfig wlan1 essid YOUR_ESSID
	pre-up iwconfig wlan1 key YOUR WEP_KEY

```

For other example eg, configuring WPA encryption see [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by mwm1 on 2007-05-21
Sweet,

Thanks to everyone who chipped in to help me. :D

---

