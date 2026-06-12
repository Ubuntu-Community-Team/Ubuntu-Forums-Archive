---
title: "Internet not working - new installation"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Nick T. on 2007-11-30
In a moment of mental illness I decided to resurrect an older 3GHz Pentium 4 that had been collecting dust for a few months. After spending a couple of hours formatting the hard drive, installing WinXP sp2, and doing an almost endless series of windows updates I sat staring at the box and wondering what to do with it….aha!....this is the way to finally learn something about Linux.

I downloaded Firefox and Nod32 and started googling. Ubuntu looked to be the way to go, so I started downloading the 700 MB .iso image from the Ubuntu site and spent the over two hour wait reading about how to do the installation; learned about MD5SUM and InfraRecorder.

The installation went impressively smoothly and I was soon looking at the Ubuntu desktop on my monitor for the first time. The Firefox icon at the top of the screen caught my eye and drew a mouse click. I was presented with the familiar Firefox window containing a welcome to Ubuntu 7.10 screen. The USB memory stick with my bookmarks was still plugged-in, so I imported them and fixed the toolbar folder; now it really looked like home! Typed in [www.google.com](www.google.com) and got a “Server not found” message.

The point of all this is to point out that this is a very clean computer….no artifacts leftover from earlier use. Also the obvious…...if I were asked if I’d been working with Linux a long time, I’d answer, “Yes Sir. All day and part of the evening!” I’m too new to even be a newbie yet.

Nothing but the facts……..

This computer is connected to a wired home network along with a Windows box, a Mac mini, and a printer. The router has an LED for each device; lit when communicating. The light for this computer is off when booted to Ubuntu….stays off during reboot to WinXP until late in the black screen that follows the Windows splash screen and precedes the Welcome screen…..and then stays on until leaving WinXP. 

I’ve found the “Network Settings” window, and after way too much diddling now has a checkmark by the “Wired connection - Address: dhcp” entry on the Connections tab; the General tab has the Host name as the computer’s name; the DNS tab has no entries in either box; the Hosts tab has some strange IP Addresses (like ::1 and fe00::0) where I’ve made one or two deletions which I failed to document…..127.0.0.? was one of them.

I’ve also found the “Devices - Network Tools” window which has a lot of information, all of which is way over my head.

Although I haven’t discovered an easy method for using the help files. I have found a number of things to try, none of which worked…..including running “sudo ifdown eth0” and “sudo ifup eth0”.

I’m really anxious to start investigating this new operating system, but it seems kings of pointless if I can’t get on the internet.

All hand holding appreciated.
  -Nick

---

### Post by jcsteele on 2007-11-30
Can you open up a terminal (Applications -> Accessories -> Terminal) and type in "lspci" and send us the output? (looking for something like "ethernet controller" etc. you can ignore the VGA lines,  that obviously dont have anything todo with your network card....  I am assuming the network card in the computer is a PCI device.

Also, the "127.0.0.1" you think you deleted is called the "loopback" device and is suppose to be there (pretty much its prevalent on any OS, windows, linux, etc.) so you might need todo some fixing later for that...for now lets see if your ethernet card is detected, etc. and what it is.

//jcs

---

### Post by Nick T. on 2007-12-01
lspci yields one applicable line:
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

The Ethernet port is motherboard implemented.

---

### Post by mayakint on 2007-12-01
Mine has the same problem.  I can't connect to the office network. It worked fine with Xandros, but it doesn't work with Ubuntu.  Mine shows  
00:04.0 Ethernet controller:  Silicon Integrated Systems [SIS] 191 Gigabit Ethernet Adapter (rev 02)

I also tried reading the forums and typed netstat -nr, but there was no address that appeared it only showed
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

(nothing follows after that)

So I'm not sure if the hardware is compatible or something.

---

### Post by baxterdog on 2007-12-01
I haven't installed an enet switch at home yet and have found that I have to reboot my cable modem when switching between my Windows desktop and Ubuntu laptop. Even worse is if I just closed the lid on the laptop after being on my work network. Then I have to log off and on too!

--Better yet would be to figure out how to use a terminal command (in ifconfig?) to assert a dhcp re-assignment!--

---

### Post by fineas on 2007-12-01
This might help 
sudo dhclient

---

### Post by Nick T. on 2007-12-01
Fineas - - I ran “sudo dhclient” in Terminal and got the following:

> 
There is already a pid file /var/run/dhclient.pid with pid 5986
Killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:30:1b:b0:b1:28
Sending on   LPF/eth0/00:30:1b:b0:b1:28
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received
No working leases in persistent database - sleeping

This is similar to the result when running "sudo ifup eth0"

---

### Post by fineas on 2007-12-01
Give me the output of:

cat /etc/resolv.conf

---

### Post by Nick T. on 2007-12-01
running "cat /etc/resolv.conf" returns nothing.

The /etc directory has an empty text file named resolv.conf which appears to have been created yesterday morning.

---

### Post by fineas on 2007-12-01
Ok, check here:
[http://ubuntuforums.org/showthread.php?t=588315&highlight=dns](http://ubuntuforums.org/showthread.php?t=588315&highlight=dns)

---

### Post by Nick T. on 2007-12-01
**Fineas - - **I read your link and went to the OpenDNS site, then did the following:

Confirmed that /etc/resolv.conf was empty
Confirmed that the DNS tab of Network Settings was empty
Added the two OpenDNS addresses to the DNS tab.  (208.67.222.222 & 208.67.220.220)
/etc/resolv.conf now has two lines: “nameserver 208.67.222.222” and  “nameserver 208.67.220.220”
Still no internet access, but now the system is very, very slow.

Changed the DNS tab to my router’s address - - 192.168.1.1 - - still no connection and extremely slow
Rebooted - - still no connection and extremely slow, LED on router still off.
Cleared DNS tab entries - - still no connection, but speed is now back to normal.

Rebooted to WinXP - - router LED is now on and internet access is normal.

---

### Post by jcsteele on 2007-12-01
if you boot with the livecd are you able to connect?

//jcs

---

### Post by fineas on 2007-12-01
First, before doing anything else, just make sure that the /etc/dhcp3/dhclient.conf file is as before following [http://ubuntuforums.org/showthread.php?t=588315&highlight=dns](http://ubuntuforums.org/showthread.php?t=588315&highlight=dns) howto
(I am reffering to the 4th step, which was
sudo cp /etc/resolv.conf.bak /etc/resolv.conf

Furthermore, let's
see if  /etc/dhcp3/dhclient.conf is ok:

Code:
sudo gedit /etc/dhcp3/dhclient.conf

Find the following line to the document (that we changed before)
prepend domain-name-servers
and replace it with

#prepend domain-name-servers 127.0.0.1;


Now, boot in windows XP (I know it's not exactly the linux way, but we just try to fix a problem without messing XP's settings :)). Click on control panel>network.Click on the icon of the internet connection. Then support tab>details. There is a number for DNS. Write it in a paper.

Reboot in ubuntu. Open the network settings. In the DNS tab put the DNS number from windows XP. In the connections tab's properties' button, choose DHCP. Make sure that the connection (if I am not mistaken, it's eth0) is ticked and wait for 1-2 minutes 

If connection is not established yet, try again
"sudo ifdown eth0" and "sudo ifup eth0"
(if eth0 is the connection that internet comes from)

If still nothing, then go to:

[http://ubuntuforums.org/showthread.php?t=282034&highlight=dns](http://ubuntuforums.org/showthread.php?t=282034&highlight=dns)

and find the "Disable IPv6 Globally" HOWTO [personally, I haven't gone so far (yet)]

If still nothing, setting a static IP address (in the network manager) maybe fix the problem. However, this should affect your XP network settings; also it is not a recommented solution if you plan to share your internet connection.

If still nothing, it's either the deletion of the loopback device or something else that I cannot help. 

I ''ll be glad if you fix your internet connection. 

Best wishes

---

### Post by Nick T. on 2007-12-02
Disconnected all cables, moved the computer to the other end of my desk, and reconnected all cables. Rebooted to Ubuntu - - unsure of how the boot went because I was out of the room. Clicked on the Firefox icon; Firefox opened and went right to the Google site. Un-freakin’-believable! My router LED for this computer is now on and internet access seems normal.

Rebooted to WinXP. The motherboard splash screen took a very long time (maybe 45 seconds instead of the usual less than 5 seconds) and then dumped me into the BIOS setup. Exited Setup and the bootup to WinXP was normal. Internet operation was normal. The long splash screen and going to Setup didn’t seem to have affected anything. Restarted WinXP and the startup was normal this time.

Rebooted to Ubuntu - - with a normal start sequence. Firefox would not connect and the router LED was out.

Powered down, disconnected and reconnected all cables, powered up a allowed the boot to Ubuntu. This time it displayed a lot a rapidly scrolling text during the startup. Internet access is normal and the router LED is on.

cat /etc/resolv.conf shows:
   nameserver 68.190.192.35
   nameserver 68.214.48.27

Here is the contents of /etc/dhcp3/dhclient.conv

#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


At this point I’ve got a working machine. It appears that all that is needed to give internet access to Ubuntu is to start Ubunto from a power-off condition. Up until now every power-off startup was to WinXP - - so it appears that windows is saying something to either the motherboard’s Ethernet controller or to the router that keeps Ubuntu from connecting. Strange. I want to give it some thought before making any more changes.

I'll attribute the odd startup to a hard drive glitch - - probably caused by a ball-bearing with a flat spot after sitting unused for several months.

The problem is NOT resolved, it’s just defined differently now.

I really appreciate your help,
   -Nick

---

