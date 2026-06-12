---
title: "No wired/wireless network connection"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by fizikz on 2007-01-14
I just installed Ubuntu 6.06 LTS (Dapper Drake), and I'm trying to establish an network/internet connection through my router. Ubuntu sees my wireless and wired hardware, but it seems I'm not being able to configure to connect. It shows the wireless and ethernet connections as activated. Then if I go into properties to try and set up the wireless settings, it detects my wireless network in the drop down box labelled "ESSID". However, I'm uncertain as to what I should enter in the "WEP" field, since I use WPA. Also, is the key Hex or ASCII? I tried putting my WPA key, and tried both Hex and ASCII options, but none of them worked. Also, when it tries to connect, I see the wifi light on my laptop blink, but even after the connection attempt is over, the wifi lights continue blinking all the way until I quit Ubuntu. 

What do I need to do? It's very difficult to do anything without internet...

---

### Post by rabid9797 on 2007-01-14
install your wireless card with ndiswrapper
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

than setup the card with WPA w/ ndiswrapper(right below)
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_enable_WPA_with_Ndiswrapper_driver](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_enable_WPA_with_Ndiswrapper_driver)

---

### Post by fizikz on 2007-01-14
In the first link, it says those steps are only to be followed if the network card is not supported. I have the Intel Pro/wireless 3945 ABG. Is this supported or not?

Should I still follow the instructions in the link?

---

### Post by rabid9797 on 2007-01-14
actually, go ahead and try this:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

install automatix, go to internet tab, choose network manager AND ndiswrapper and let automatix install them for you.

after that finishes go to system -> Network Tools and try to configure from there.

---

### Post by fizikz on 2007-01-14
I installed automatix2, but when I try to run it, I get an message saying that it did not find an internet connection, and asking me to run it again after I've established one. :rolleyes:  What now?

---

### Post by misha680 on 2007-01-15
You could try to install network manager by going into System->Administration->Synaptic Package Manager. Search for network-manager and install the packages network-manager and network-manager-gnome (I don't know if these are on the Ubuntu CD or not, if they are not and you have no network you might not be able to do this. In this case, try going to the URL [https://launchpad.net/ubuntu/dapper/+source/network-manager](https://launchpad.net/ubuntu/dapper/+source/network-manager) on another computer, there you should find the "deb" packages for your architecture, I assume i386. Get all the ones that do not have a "-dev" or "-dbg" at the end, put it on your Windows drive or a USB drive, then plug it into your Ubuntu computer and you can install each deb by double-clicking on each deb, but you will have to do this in the right order or it won't let you). Anyway, now press Apply and network-manage rshould be installed. Log out and log back in, and you will see the network manager icon in the top right hand panel (if not, just press Alt-F2 and type in:
```
nm-applet --sm-disable
```). Now, click on that icon, go down to "Connect to Other Wireless Network" and you will be able to put in your WPA information.

Hope this helps.

Misha

EDIT: It might be easier if you have to download from another computer it might be easier to just get my CVS NetworkManager packages (compiled from a newer codebase, not as stable, but should be easier because you just need to download one file)... see here [http://www.ubuntuforums.org/showthread.php?t=235655](http://www.ubuntuforums.org/showthread.php?t=235655)

---

### Post by r4ik on 2007-01-15
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

Good luck !

---

### Post by fizikz on 2007-01-15
For:
sudo apt-get install network-manager-gnome

I got: 
E: Couldn't find package network-manager-gnome

And then for:
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

I get:
No theme index file in '-f/usr/share/icons/hicolor'.
If you really want to create an icon cache here, use --ignore-theme-index.



As for downloading the '-deb's from misha680's link, I did this. I downloaded 4 files. However, one of them gave me the following message: 
"conflicts with the installed package 'libnm-glib0'"

I'm not sure exactly what I was doing, so it's possible I did something wrong. 

Your continued help is greatly appreciated.

---

### Post by r4ik on 2007-01-15
Sorry for beeing late had to be elsware

First try to get the wired connection going.

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)


I think you have not got extra repositories enabled.

Please read this guide and try agian.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

There is more there that might interest you.

Once you got internet concider an upgrade to Edgy you're
Intel Pro/wireless 3945 ABG is supposed to work out of the box.
Upgrading can be done by,
Open a terminal and do a sudo apt-get update then copy and paste this code in terminal and your machine will do the rest::$ gksu "update-manager -c"

Good luck !

---

### Post by fizikz on 2007-01-17
Well, I'm not sure what I did, but I got the wired connection working. I downloaded and installed ndiswrapper and Network Manager. I entered my SSID, selected WPA Personal, and entered the password, but it failed to connect. I also got Wireless Assistant, and it is able to detect my wireless network, but can't connect. Wireless Assistant only asks for WEP key, and not for WPA, so that may be a factor. Nevertheless, it seems the wireless is detected, but so far I've never been able to connect to it. Anything else I could try at this point?

---

