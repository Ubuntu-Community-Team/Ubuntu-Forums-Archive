---
title: "setting up a wireless network"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Mostlyharmless42 on 2007-06-21
hey, i just got a new lynxes card and it was detected pretty quickly, but i don't know how to get it to connect to my wireless hotspot. Can anyone give me a quick network setup guide??  I've never really understood networking very well...

---

### Post by Mostlyharmless42 on 2007-06-21
bump

---

### Post by PartisanEntity on 2007-06-21
Hi, do you know which version of Ubuntu you have installed?

---

### Post by Mostlyharmless42 on 2007-06-21
6.10, i think that is Edgy Eft

---

### Post by PartisanEntity on 2007-06-21
I would recommend Network Manager:

>    1.

      Applications, Add/Remove Programs
   2.

      Find Network Manager in the Internet section
   3.

      Check the adjacent box to select Network Manager for installation
   4.

      Click OK
   5.

      Log out and back in again
   6.

      If you don't see the Network Manager icon you may need to add the Notification Area to your panel

From here:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Mostlyharmless42 on 2007-06-21
when i try to select the box to install the network manager i get this error

"Network Manager cannot be installed on your computer type (i386)"

"Either the application requires special hardware features or the vendor decided to not support your computer type"

---

### Post by Mostlyharmless42 on 2007-06-21
bumpity bump bump

---

### Post by dhruva023 on 2007-06-21
try to install it from synaptic,

---

### Post by Mostlyharmless42 on 2007-06-21
...can't figure out how to run synaptic...

---

### Post by PartisanEntity on 2007-06-21
System > Administration > Synaptic Package Manager

---

### Post by Mostlyharmless42 on 2007-06-21
i looked at the list in synaptic and the only thing it will let me do w/ anything on the list is either.

Mark for removal or Mark for complete removal

---

### Post by PartisanEntity on 2007-06-21
Are you sure you are not clicking on packages that are already installed?

The green labelled ones are installed already.

---

### Post by Mostlyharmless42 on 2007-06-21
They are all green...

If it makes a difference this computer doesn't have an internet connection...

---

### Post by PartisanEntity on 2007-06-21
Yes you will need a working internet connection to download and install the packages. It is possible to download the packages manually from your Windows machine for example and then copy them to your Ubuntu installation and install them.

The packages you will need are:

[dhcdbd_1.14-2ubuntu2_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdhcdbd%2Fdhcdbd_1.14-2ubuntu2_i386.deb&md5sum=f597e9322731e08b68815383d274bac2&arch=i386&type=main")
[libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibn%2Flibnl%2Flibnl1-pre6_1.0~pre5%2Bsvn21-2ubuntu2_i386.deb&md5sum=0d836551f19893b6dbc34888b173d809&arch=i386&type=main")
[libnm-util0_0.6.3-2ubuntu6_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Flibnm-util0_0.6.3-2ubuntu6_i386.deb&md5sum=35f0369504c376261c6cddc76e29c64d&arch=i386&type=main")
[network-manager_0.6.3-2ubuntu6_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager_0.6.3-2ubuntu6_i386.deb&md5sum=522cade5b931785517c0fb2bb7035a1e&arch=i386&type=main")
[network-manager-gnome_0.6.3-2ubuntu6_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager-gnome_0.6.3-2ubuntu6_i386.deb&md5sum=1f857fb5abaa57675e4695baf66289b5&arch=i386&type=main")

Once you have downloaded these packages and copied them to your Ubuntu installation you can simply double click on each of the .deb files to install it.

---

### Post by Mostlyharmless42 on 2007-06-21
ok, i have those packages installed.  What do i do now to set up my network

---

### Post by PartisanEntity on 2007-06-21
You should now see the network manager icon in the notification area of the top panel (on the right side of the screen). The icon looks like two computers.

If you left-click on it, it should show you a list of the wireless networks in your area. You should hopefully see your own network, you can then click on it to connect to it. If you are using encryption then network manager will pop up a window where you can enter the relevant information to connect.

Once the connection has been established, network manager will ask you to set a passphrase, you will have to enter this passphrase every time you wish to connect to your network.

---

### Post by Mostlyharmless42 on 2007-06-21
ok, the icon is there, but it doesn't seem to see my wireless card.  the card appears in the device manager.  When i go to System>Administation>Networking, it says under wireless connetion that "this network interface is not configured"  Under properties it asks for network name (ESSID).  what should i put there??? I've tried the name of the network i'm looking for, but that didn't work.

---

### Post by PartisanEntity on 2007-06-21
Is your router set to broadcast SSID? Do you use any kind of encryption?

---

### Post by Mostlyharmless42 on 2007-06-21
No encryption but it is set up to not use SSID

---

### Post by PartisanEntity on 2007-06-21
Then that would explain why your router is not showing up in the list.

Left-clic on the network manager icon and select: Create New Wireless Network

Enter the ESSID any other relevant information and hopefully you should be connected.

---

### Post by Mostlyharmless42 on 2007-06-21
when i left click all it give me is a grayed out "wired network"

---

### Post by PartisanEntity on 2007-06-21
Try restarting the computer.

---

### Post by Mostlyharmless42 on 2007-06-21
restarting didn't change anything

---

