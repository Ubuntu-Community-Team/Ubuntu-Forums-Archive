---
title: "Newbie WPA problems"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Rollotamasi on 2007-01-21
I've been working getting my WPA working all weekend have am starting to think its never going to work.  My broadcom card is installed (That was a adventure) My network manger is installed (Another adventure) And If I right click on my network manager I see the networks.  Problem is I cant get WPA working.  I don't even see a spot to input a WPA key.  If I select one of the networks it just tries to connect, doesnt ask me for a key or anything.  I have tried so many of the guides at this point I cant remeber what I have done and what I havent.  Can anyone please assist me.  I dont want to go back to xp.

---

### Post by r4ik on 2007-01-21
Tried this one ?

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

### Post by Rollotamasi on 2007-01-21
Never mind, just got it working.

---

### Post by Rollotamasi on 2007-01-21
> **r4ik said:**
> Tried this one ?

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

Thanks for the reply but I just figured it out.  Was so easy iI'membarrassed to say what was wrong...

---

### Post by Rollotamasi on 2007-01-21
> **r4ik said:**
> Tried this one ?

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

Thanks for the reply but I just figured it out.  Was so easy I'm embarrassed to say what was wrong...

---

### Post by r4ik on 2007-01-21
Glad it works !
what was wrong ?

---

### Post by featherking on 2007-01-21
You should left click not right click on the network manager icon to see the available networks. When you do that the network name will appear with a little shield (if using wep/wpa) and a signal strength bar. Then you left click there to start it connecting. If it tries to connect automatically and not ask you for a password that means it already has a password stored for that network and its going to try and use it. If that password doesnt work after a bit it will time out and ask you for a password for that network.

If you want you can input everything manually by clicking 'connect to other wireless network' then you input the name and select wpa and put in your passphrase and then it will use that info to try and connect

If you still cant connect to wpa, i would check if you have wpasupplicant installed in synaptic. If it still wont work check this [[COLOR="Red"]post[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=2024518&postcount=4") to make sure your network manager is setup correctly.

Give that a try and see what happens..

---

### Post by Rollotamasi on 2007-01-21
> **r4ik said:**
> Glad it works !
what was wrong ?

It has actually been working since I reinstalled the network manager.  Problem was it was poping up the window to put the WPA key in behind my browser window so I dint see it so I thought it wasnt working...:lolflag:   Like I said, very embarrassing lol.  Now all I have to do is get vbox working and I'm in buisness!

---

