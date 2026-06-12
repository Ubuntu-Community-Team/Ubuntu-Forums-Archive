---
title: "Wireless in MacBook Pro"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by rcx_6000 on 2008-05-11
Hey all. I just tried out ubuntu 8.04 on my macbook pro and am currently goofing around on the live cd while i decided how to install it. I am the admin of a 7 computer network and am experimenting with wireshark. I am using a macbook pro V1.0 and everything work out of the box. now when i do a scan in wire shark with promiscous mode i only get traffic being sent by the router and not the traffic going from computer to router. this is over wifi. i have madwifi installed and have followed as many tutorials as i could find with no luck. Does anyone know how to get what i want working. I have tried ath0 and wifi0 with no luck and making a interface in monitor mode with wlanconfig as ath1 doesnt even show up in wireshark.

---

### Post by rcx_6000 on 2008-05-11
and also it only shows data on my network

---

### Post by russo.mic on 2008-05-12
I've never been able to get madwifi to work reliably.  I recommend ndiswrapper for atheros or broadcom hardware, the drivers of which can be found in bootcamp or on the OS X CD.  There is also torrents available of the drivers on "certain" websites.


Russo

---

### Post by cyberdork33 on 2008-05-12
> **russo.mic said:**
> I've never been able to get madwifi to work reliably.  I recommend ndiswrapper for atheros or broadcom hardware, the drivers of which can be found in bootcamp or on the OS X CD.  There is also torrents available of the drivers on "certain" websites.


Russo
If you know what you are doing, you can also get them out of here:
[http://www.apple.com/support/downloads/bootcampupdate21forwindowsxp.html](http://www.apple.com/support/downloads/bootcampupdate21forwindowsxp.html)

Hint: Unzip the exe

---

### Post by Jammy4041 on 2008-05-12
> The MacBook Pro uses an Atheros wireless chipset that is not compatible with the current stable MadWifi driver. However, the prerelease version of the driver is compatible, but is unstable in some cases. With proper installation and some modifications, it is adequate for everyday use. However, the Atheros HAL is binary and is not considered open-source software.

To install the prerelease MadWifi drivers, you can chooose to use daily snapshots or Subversion.

Using Subversion (be patient with the checkout, it may take a while):

```
sudo apt-get install build-essential subversion automake autoconf
svn co http://svn.madwifi.org/madwifi/trunk madwifi
cd madwifi
make
sudo make install
sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/modprobe wlan_scan_sta\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/iwpriv ath0 bgscan 0\nexit 0/' /etc/rc.local
```

At this point the driver is installed and should work and the internal wifi will be enabled after reboot. Alternatively, you can skip the reboot and use these commands to insert the driver into the running kernel:

```
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo iwpriv ath0 bgscan 0
```

Finally, the MadWifi driver will prevent you from resuming after suspend-to-ram. To fix this, edit /etc/default/acpi-support and add the ath_pci driver to the MODULES variable, like so:

# ...
MODULES="ath_pci"

# ...

(I got this from [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) . This may help)

---

### Post by cyberdork33 on 2008-05-12
additionally, you should add ath_pci to /etc/default/linux-restricted-modules-common to prevent Ubuntu from trying to use the Ubuntu-supplied module.

---

### Post by ReneB on 2008-05-12
Hi Cyberdork33 

how does one do this:
''additionally, you should add ath_pci to /etc/default/linux-restricted-modules-common to prevent Ubuntu from trying to use the Ubuntu-supplied module.''

can you do it in Software Sources or should you edit some config file?

thanks

---

### Post by cyberdork33 on 2008-05-12
> **ReneB said:**
> Hi Cyberdork33 

how does one do this:
''additionally, you should add ath_pci to /etc/default/linux-restricted-modules-common to prevent Ubuntu from trying to use the Ubuntu-supplied module.''

can you do it in Software Sources or should you edit some config file?

thanks
Open the file  with a text editor (/etc/default/linux-restricted-modules-common)
Then you literally add "ath_pci" to the location indicated in the file.

Read the section titled "Madwifi and Linux-Restricted-Modules" here:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by rcx_6000 on 2008-05-12
i got another quick question. i have read most of the install tutorials for mac already. In my case. i have a 80 gb drive with 10 gb free. bootcamp dont work for some reason to make a partition to format for linux. and i have no place to backup my drive to in order to reformat my drive with mbr and restore my mac partition. what is the most reliable way to install linux in my case?????

---

### Post by sunbird on 2008-05-15
> **cyberdork33 said:**
> additionally, you should add ath_pci to /etc/default/linux-restricted-modules-common to prevent Ubuntu from trying to use the Ubuntu-supplied module.

[The madwifi page]("http://madwifi.org/wiki/UserDocs/Distro/Ubuntu") says you add "ath_hal" not "ath_pci." But I know the module for wifi is ath_pci... so I guess I'm just wondering why it says _hal on the madwifi page...

My madwifi has been working okay without any mods to this file, but sometimes I get dropped connections.

---

### Post by cyberdork33 on 2008-05-15
actually it probably should be ath_hal. ath_pci relies on the ath_hal module to work.

---

### Post by rcx_6000 on 2008-05-18
i got ubuntu 8.06 with madwifi prerelease installed and wireshark still only sees traffic leaving the router. any help would be nice.

---

### Post by rcx_6000 on 2008-05-19
it works now. i think its because its installed and not running from the live cd

---

### Post by rcx_6000 on 2008-05-19
nvm

---

### Post by rcx_6000 on 2008-05-19
got it

---

### Post by pierce_ on 2008-12-13
So, are there any follow ups on this?  Did you manage to fix this, and if so, how?  I am having the same problem.  It looks to me like somewhere along the line something is dropping all packets that are not sent from the access point.

When I create a device in monitor mode, I get 80211 frames from everyone, but when I have a device in managed mode, all I can see are packets from myself, and the access point.  Even when the device is running +promisc +multicast +allmulti etc.

This is not the expected behavior of a wireless device.  All other cards that I have used (broadcom/orinoco etc) show all ethernet frames from all clients on the wireless network as soon as the device is put into promiscuous mode.

---

