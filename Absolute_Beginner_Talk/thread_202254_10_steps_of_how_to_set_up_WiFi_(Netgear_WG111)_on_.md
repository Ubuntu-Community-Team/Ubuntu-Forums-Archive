---
title: "10 steps of how to set up WiFi (Netgear WG111) on Ubuntu"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Oputres on 2006-06-23
[COLOR="Red"]*This post was updated January 2007*[/COLOR]

Hi, this has been an issue for me along time now. I've tried to setup my Netgear WG111 USB device in Xandros, Kubuntu and Suse but never made it. Then I tried Ubuntu and after several hours I finally got it working! This is how I did it!

But before we begin let me tell you about the necessary Ndiswrapper. Ndiswrapper is a utility that alows you to use Windows drivers on your Linux. This is very useful since there are not many manufacturers out there that supplies Linux drivers.

For a successful configuration you will need:
* To configure your Wireless router to broadcast your ESSID and disable the protection to eliminate any problems this may cause.
* Your Ubuntu installation CD.
* Your Netgear CD containing the Windows drivers. This was the only one that worked for me.
* A cabled connection to the internet.

OK, let us begin:

1. Open the Synaptic package management tool from System -> Administration and search for ndiswrapper-utils, ndisgtk and Wifi-radar. Install these! (If you can't find them you must activate the Universe repositories in Settings -> Repositories). Ndisgtk is a graphical tool for Ndiswrapper so you don't need to write command lines in the Terminal. It was also the only way for me to get a correct installation of the drivers. Wifi-radar is a program that list availible Wlan when you're done.


2. Blacklist Ubuntus existing drivers by typing "sudo gedit /etc/modprobe.d/blacklist" in the Terminal (Program -> Accessories -> Terminal) and add the following lines at the bottom of the file:

#Netgear conflicting drivers
blacklist islsm
blacklist islsm_pci
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b


3. Check for any earlier installed drivers by typing "sudo ndiswrapper -l". If you found a driver you want to remove just type "sudo ndiswrapper -e driver-name"


4. Install the Netgear Windows driver by starting ndisgtk from System -> Administration -> Windows Wireless Drivers and press "Install New Driver". Choose the correct .inf file from your CD containing the drivers, in my case it is the netwg111.inf from my Netgear CD.


5. Return to the Terminal and type in the following lines:
"sudo depmod -a"
"sudo modprobe ndiswrapper"
"sudo ndiswrapper -m" (Perhaps it will say "modprobe config already contains directive" but carry on)

and finally:
"sudo gedit /etc/modules" where you add "ndiswrapper" at the bottom of the file.

(To be honest, I don't know exactly what this does but I think it has something you do to have Ubuntu look for the device on every startup.)


6. Shut down your computer, insert the USB device and start your computer again.


7. Check if Ubuntu has found your device by typing "ndiswrapper -l" in the Terminal. If it says "netwg111 (or equal) driver installed, hardware present" then you're ok! If not, abort and retry from step 3.


8. Start Windows Wireless Drivers (ndisgtk) from System -> Administration. Does it say Hardware present: Yes? If so, great! Then press Configure Network and press Properties for Wireless connection where you activate this connection. Type in your ESSID (same as your router) and leave the rest untouched if you like me disabled the protection. Now your USB device should have the blue light on.


9. Start Wifi-radar from Program -> Internet. WiFi Radar will now show that you are connected to your Wlan and also display all the other WLANs in the area. (If it's a blank page and you know there should be at least one Wlan something isn't right, try rebooting your computer and retry from step 7).


10. Inactivate your cabled connection in System -> Administration -> Network and disconnect your cable. Enjoy your wireless surfing!


Don't forget to protect your connection again! The WPA-PSK protection seems to require quite a lot of work so why don't you start with the WEP alternative. If you in WiFi Radar choose to Edit your profile you see that there are some fields for keys etc. Havn't looked into this yet though.

And finally, this link was very helpful for me in this case:
[https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)
And don't miss this link about the "Windows Wireless Drivers" (ndisgft tool):
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

---

### Post by Apple 101 on 2006-06-23
You can find information about WPA support from these forums or from Google.

---

### Post by Oputres on 2006-06-23
Deleted

---

### Post by eternalsword on 2006-07-15
my guide at [http://www.ubuntuforums.org/showthread.php?t=212365](http://www.ubuntuforums.org/showthread.php?t=212365) also contains info about modules that need to be blacklisted might want to check that out.

---

### Post by paul6 on 2006-10-14
deleted

---

### Post by morry on 2008-06-01
Thanks Oputres !! Champion... your guide worked a treat.

---

