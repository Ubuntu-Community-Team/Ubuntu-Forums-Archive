---
title: "Changing the setting from WEP to WPA"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by kylesrv on 2006-09-10
I just installed a wireless network for my 2PC in my home.  When I attempted to install the router I was informed my laptop did not have WPA but I understand WPA is more secure.  How do I change from WEP to WPA

---

### Post by Sandlst on 2006-09-10
You can open a web browser (after being connected to your router) and type in something like ```
192.168.1.1
```It should ask you for a name/password that is probably in the router manual, from there hopefully there will be a 'security' tab or something you can go to to specify it to use WPA. Out of curiosity how did you determine your laptop does not have wpa? If your laptop does not have wpa in its wireless hardware you will not be able to connect to it wirelessly.  Also, in ubuntu you need the package 'network mananger' to be able to connect to wpa networks, go [here]("http://doc.gwos.org/index.php/Network_Manager_with_WPA") to see how to set it up if you need to.  Good luck, post back if you have any problems.

---

### Post by crazymonkey on 2006-09-10
If I get it right your router is set to use WPA but your Ubuntu laptop don't allow you to use WPA?

If it the case you might want to install network-manager. It allow you to easily use WPA and allow easy roaming between wireless hotspots.

```
sudo apt-get network-manager network-manager-gnome
```
*If you use KDE change gnome to kde

Then logout and login again and you will see the network-manager icon in your notification area, if you click on it you should see the available wired/wireless connections available. Select your WPA connection and it will open a windows asking you to enter you WPA key (or WEP key for a WEP network).

[IMG]http://ubuntuforums.org/gallery/data/500/wl1.png[/IMG]

After this you should be alright.

The nice thing about this is that if you have several wireless connections configured in network-manager it will automatically choose the available one or the one with the best signal.

---

### Post by Fingolfin269 on 2006-09-10
I can't get this to work.  I followed your instructions and I do have a new network-manager icon (2 of them now in the top right?) but I still only have 3 security options to choose from and ALL of them are WEP.

I found another guide and followed it as well and it did not work either.  ARGH. :p

---

### Post by crazymonkey on 2006-09-10
First of all you should make sure that your wireless interface supports WPA (if you dual boot XP and ubuntu try to boot in XP and connect with WPA) because some older hardware might not support WPA. Also, can you connect using WPA with your other computer? Whats OS is running on your second computer? 

If you are sure that you card supports WPA and that your router is well configured try the following :

Go in System/Preferences/Session and check in the Startup Programs tab, you should see an entry saying nm-applet --sm-disable. Edit the line to remove the --sm-disable part.

[IMG]http://ubuntuforums.org/gallery/data/500/sessions.png[/IMG]

You should also remove the Network Connection applet since you can't use both. Remove the one at the right on the screenshot.

[IMG]http://ubuntuforums.org/gallery/data/500/nm-applet.png[/IMG]

Make sure you also have the wpasupplicant package to enable WPA support. It was installed by default on my system but you should make sure you have it.

```
sudo apt-get install wpasupplicant
```

After checking all this reboot your computer and let us know if it worked 8)

---

### Post by Fingolfin269 on 2006-09-10
I tried all of that and get this message when attempting to connect to my home wireless network:

> The requested wireless network requires security capabilities unsupported by your hardware.

I have wpasupplicant and the most updated network manager.  I made that chance to the nm applet as well.

Do you think I need to do something else concerning my wireless USB adapter (Linksys WUSB54G)?  I am assuming it works okay because I have no problem detecting wireless networks but I cannot connect to anything due to WPA so I cannot say for sure.

---

### Post by crazymonkey on 2006-09-10
Unfortunatly it seems that your wireless adapter doesnt support WPA.

Thats what I got from a reseller website:
> 
_**Linksys WUSB54G**_
**Security Features:**
 - WEP Encryption
**WEP Key Bits:** 64, 128-bit


If your adapter supported WPA it would have been listed under the security feature section...

If you just bought it try to exchange it for an adapter that supports WPA...

Good luck!

---

### Post by Fingolfin269 on 2006-09-10
Weird, it worked just fine connecting to WPA when I Windows XP running on this laptop.  Strange. I guess I can try this Belkin F5D7010 and see if it will work.

---

