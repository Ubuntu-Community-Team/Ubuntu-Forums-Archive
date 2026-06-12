---
title: "WPA Problems with Dapper"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2007-01-09
](*,) 

I think I may have already posted a thread on this subject, but I am not sure.

I am having a heck of a time getting my wireless connection setup in Dapper.  I have tried every how to guide I could find and have gotten absolutely nowhere.  As far as I can tell it seems like it is near impossible to get Ubuntu to connect to a wireless network using WPA.

I decided to use WPA because it is more secure and I am also running a dual boot with Windows XP(I am using Windows as a glorified gaming client because it is just easier than trying to force my Windows games to run on Linux) and I could not get WEP to work at all in Windows.  At this point it is looking like I can only get a wireless connection working in one OS or the other and that I have to choose WEP in Ubuntu or WPA in Windows.  I only have a connection in Ubuntu right now because I am running a 50 foot ethernet cable to the router.

If anyone had any helpful advise on how I can get WPA to run in Ubuntu that does not involve making a blood sacrifice to my PC I would appreciate it.  I am trying very hard to keep my sense of humor about this, but this is really starting to drive me nuts. 


Thanks in advance,


Dan

---

### Post by r4ik on 2007-01-09
Try,

 How to Configure Ubuntu/Kubuntu with WPA using Network-Manager

Ubuntu Dapper in typical cases can configure WPA to work out of the box with minimal hassle. You'll need to install network-manager.


For Ubuntu:

sudo apt-get install network-manager-gnome

For Kubuntu (will install knetworkmanager):

sudo apt-get install network-manager-kde

Logout/Reboot.

Ubuntu users should now see the NetworkManager Applet in the Gnome notification area. Kubuntu users will probably have to run knetworkmanager before they see NetworkManager in the systray.

If instead, you get a "The NetworkManager applet could not find some required resources. It cannot continue." message, then:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

Once Network-Manager is installed, click on the NM icon in the notification area (default is at the top right of Ubuntu/Gnome). Choose your network, then enter your passphrase. Type a password for the keyring, and you're set.

If you don't see your network, click "Create New Wireless Network...", type your essid/networkname, then choose "WPA Personal" for wireless security.

    * Note: If you installed Kubuntu then installed ubuntu-desktop & network-manager-gnome, you may not be able to use network-manager in Gnome, if at all. In this case, you may have to use WPA Supplicant and do some manual editing of conf files to get WPA up and running. 

    * Note: When you first log into Gnome/KDE, the keyring application will ask for a password. Future revisions of Network-Manager should resolve this. 

Seems to simple to me but who knows ?

Good luck !

---

### Post by wieman01 on 2007-01-09
If that does not work, try the HOWTO in my signature. It's good to get started.

---

### Post by ndworecki on 2007-01-10
Thank You this worked!!

---

### Post by r4ik on 2007-01-10
Congrats !

---

### Post by DanFromWinterpeg on 2007-01-10
Hi again,

The trouble is that I can't get Network Manager to even give me the option of setting up a WPA wireless network,

I have downloaded the WPAsupplicant which seems to have done absolutely nothing as far as I can tell and The Network Manager won't acknowledge anything but the ethernet connection with the 50' CAT5 cable I am using  right now so that I can get a connection at all.


I also downloaded ndiswrapper like it suggested in that "How To" guide, but what the heck am I supposed to do with it?

The ONLY thing on my system that will even give me the option of a WPA connection is Wi-Fi Radar.  But when you select WPA it asks for a "driver"  which I assumed was the WiFi NIC driver.  I entered "MadWiFi" since everything I have come across says my Dlink WDA 1320 uses that driver.  The Device Manager lists my WDA 1320 as Unknown Device "Atheros inc." is listed as the chipset manufacturer. I do not know for sure if that is relevant but I figure the more info I can provide the better

When I try connecting to my WPA network using WiFi Radar it tells me it is connected to my network, but it cannot pull a valid IP address.


Any suggestions?

---

### Post by jml on 2007-01-10
Just to clarify.  Dapper Drake does not include the applications network-manager and network-manager-gnome by default.  The application included by default is net-app and is not the same.  So be sure that you are using the correct app.  Not to insult you, but this bit confused me for quite some time until I realized my error.  The default application does not support WPA.

If you still have problems, I would suggest upgrading to Edgy Eft  (6.10)  It seems to handle wireless better for some cards.  I couldn't get WPA working with my hardware until I upgraded to 6.10.  Good luck.

Joe

---

### Post by r4ik on 2007-01-10
deleted

---

### Post by DanFromWinterpeg on 2007-01-11
Hello again,

I think I found part of the problem.  It would appear that Network Manager does not even detect my Wireless NIC.  It would seem that as far as Network Manager is concerned I only have an ethernet NIC in my PC.  I installed the Windows XP driver using ndiswrapper at one point but what now?  Nothing seems to have changed a wit.

I would try upgrading to Edgy, but every version I have tried to install, the Installer consistently hangs scanning my HDD partitions at exactly 50% at which point my PC locks up completely requiring a hard reset.

---

