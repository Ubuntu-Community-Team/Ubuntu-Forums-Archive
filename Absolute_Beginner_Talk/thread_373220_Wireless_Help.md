---
title: "Wireless Help"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by darkfarmer on 2007-03-01
Hello, I am new to Linux, and I have no clue about how to connect to my wireless router. I had no trouble at all using Windows XP to connect to the internet. However, with Ubuntu, I am at a loss.

I have an Intel Pro/wireless 2100 802.11b card, and am currently using Ubuntu 6.10

I have tried using the GUI setup (System, Admin, Network) to set it up. I put all the necessary information (ESSID, Network key, etc), and disabled the wired connection. When I go to the Network Monitor, I set it as eth1 (which I assumed to be the wireless network). However, it can only send, and not recieve. Internet does not work. 

Any help would be greatly appreciated!

---

### Post by mahy on 2007-03-01
Download the network-manager and try it out first.

---

### Post by darkfarmer on 2007-03-01
Sorry, I do not know how to install files using the command line, I am new to it. 

I have copied the files NetworkManager-0.6.4.tar.gz from [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/)

However, I am not sure what the error "E: Couldn't find package network-manager-gnome" means when I use the command "sudo apt-get install network-manager-gnome". I have even tried "sudo apt-get update", which brings up a gigantic list of errors about not being able to connect to us.archive.ubuntu.com and whatnot. 

Trying "apt-get update" brings up an error about not being able to "open lock file var/lib/apt/lists/lock (13 permission denied). 

Are you supposed to copy the NetworkManager-0.6.4.tar.gz file somewhere so the computer would find it?

---

### Post by Maestro23 on 2007-03-01
> **darkfarmer said:**
> Sorry, I do not know how to install files using the command line, I am new to it. 

I have copied the files NetworkManager-0.6.4.tar.gz from [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/)

However, I am not sure what the error "E: Couldn't find package network-manager-gnome" means when I use the command "sudo apt-get install network-manager-gnome". I have even tried "sudo apt-get update", which brings up a gigantic list of errors about not being able to connect to us.archive.ubuntu.com and whatnot. 

Trying "apt-get update" brings up an error about not being able to "open lock file var/lib/apt/lists/lock (13 permission denied). 

Are you supposed to copy the NetworkManager-0.6.4.tar.gz file somewhere so the computer would find it?

That .tar.gz file is a source file.  Not recommended for people new to linux, since you have to compile the program from scratch.

Two things you can do:

> Synaptic(GUI): Open it up and search for network-manager.  Once you find it, you can mark it for installation.

or

Command line:  sudo aptitude install network-manager


Installing in Ubunut: 
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Good luck.

---

### Post by darkfarmer on 2007-03-01
I have tried going through Synaptic to search for Network Manager. However, I cannot find it.  When I try the reload function to get new repositories, it keeps trying to download them (but I have no internet connection!) So, it always gives off errors. What should I do? I just want to get on the internet :cry:

---

### Post by sanderella on 2007-03-01
I have the same problem. My new Dell Inspiron laptop would connect to the wireless with windows XP but not with Ubuntu. Nobody seems to know the answer. I'll be interested to see if you get any success. On Windows XP, my wireless connection has been stopped by Microsoft, with a message to the effect that I have chosen not to use the Windows wireless manager. Now I can't get connected on Windows or Ubuntu. I am not one for conspiracy theories, but I am beginning to suspect that Microsoft softwear is blocking my access. 
Next week I am going to Hampshire LUG, going to totally uninstall any Microsoft stuff, and see if it's any better. I'll keep an eye on your thread.

---

### Post by bastiegast on 2007-03-01
[http://packages.ubuntu.com/edgy/net/network-manager]("http://packages.ubuntu.com/edgy/net/network-manager")

There you can find deb files, install them with ```
dpkg -i path-to-deb-file.deb
```, you need network-manager and network -manager-gnome

---

### Post by sanderella on 2007-03-01
Quote: I set it as eth1

Also try eth0

Good luck!

---

### Post by darkfarmer on 2007-03-01
I have downloaded the Gnome frontend deb file, but it says that "dependency is not satisfiable: libnm-util0".

I installed that, but now it says "dependency is not satisfiable: network-manager".

Please help!

@sanderella, I have already tried using network monitor and setting it as eth1. No go. Only sending, but not recieving.

---

### Post by bukwirm on 2007-03-01
What is the output of these commands?
iwconfig
ifconfig

---

### Post by darkfarmer on 2007-03-01
asun@Sun-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"HEXLink"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:CC:5B:98   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

sun@Sun-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:0D:98:65:CB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:04:23:85:23:4B  
          inet6 addr: fe80::204:23ff:fe85:234b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:115 dropped:115 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4224 (4.1 KiB)
          Interrupt:11 Base address:0xa000 Memory:c2005000-c2005fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


Also, I have installed the network manager gnome and ubuntu deb files. However, the icon in the task bar does not allow me to configure anything, other than enabling network.

---

### Post by bukwirm on 2007-03-01
OK, try the following:

Make sure your router is configured to allow wireless access.
Make sure you are either not using encryption or you are using WEP (WPA will not work with Linux)

Run these command, replacing the stuff in <>

sudo ifdown eth0
sudo ifdown eth1
sudo iwconfig eth1 essid <your network name> key <your wireless key>
sudo ifup eth1

See if you can connect to the internet wirelessly.
See if you can connect to your router wirelessly.

Note: this will turn off your wired connection. To restore it, run "sudo ifup eth0"

---

### Post by darkfarmer on 2007-03-01
I tried using the guide that gotgenes provided

[http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945](http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945)

However, when I reach step 6, I go to my file, but it doesn't allow me to modify the file (read-only).

This is the same as step 3, where my computer does not allow me to add the repository. Am I doing something wrong by using the text editor?

I skipped the step because I manually installed it by double clicking the gnome network manager.

Please help!

EDIT: I am using WEP encryption.

EDIT 2: @bukwirm, I tried it, but it doesn't work. It says No DHCPOFFERS recieved. No working leases in persistent database.

---

### Post by darkfarmer on 2007-03-01
Sorry for the double post, but I have everything all figured out now!

A big thank you to all the people that helped me!

---

