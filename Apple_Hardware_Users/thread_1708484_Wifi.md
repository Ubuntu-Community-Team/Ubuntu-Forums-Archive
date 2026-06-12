---
title: "Wifi"
date: 2011-03-16
forum: Apple Hardware Users
---

### Post by canhoto on 2011-03-16
Hi. 

I just managed to have Ubuntu working on my Power Mac G4 (with the precious help of linuxopjemac !) and I have a new problem: my home wireless network is detected, but when I enter my WEP (hexadecimal) password (the same I use with the same computer but with Mac OS on another drive), it doesn't connect. It's always asking me again for the password. I typed it several times, I changed the "password type" (not on the router, of course), I retried with the correct password type, and it never connects.

(Fortunately I still have an ethernet cable connected to a Macbook, and I can have internet with Ubuntu; but I would like to have it wireless).
Any ideas aout this?

---

### Post by rsavage on 2011-03-17
Try this [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143)

Please report back what worked for you and what card you have e.g. airport classic or extreme.

---

### Post by canhoto on 2011-03-17
> **rsavage said:**
> Try this [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143)

Please report back what worked for you and what card you have e.g. airport classic or extreme.
I have a classic airport. I installed wicd (with Ubuntu Software Center) and I always had the "bad password" message. Afterwards I removed the network-manager (with Synaptic), I restarted and wicd didn't even find the networks...

So, I'm still using ethernet exclusively.

I really like Ubuntu; even if I'm not convinced that it will replace Mac OS in my life... I would like to be convinced!
But it really is complicated (not the UI, which is nice, but all these problems... first the screen resolution, now the wifi connection...)

---

### Post by rsavage on 2011-03-17
Can you open up a terminal and give me the output of the following commands please?

dmesg | grep airport

ls /lib/firmware/agere*

groups

---

### Post by canhoto on 2011-03-17
[QUOTE][[   17.091693] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   17.091842] airport: Physical address 80030000
[   18.295773] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0000
[   18.295913] airport 0.00030000:radio: Station identity  001f:0001:0008:0046
[   18.295930] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
[   19.230742] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0000
[   19.230883] airport 0.00030000:radio: Station identity  001f:0002:0009:0030
[   19.230901] airport 0.00030000:radio: Firmware determined as Lucent/Agere 9.48
[   19.230914] airport 0.00030000:radio: Ad-hoc demo mode supported
[   19.230925] airport 0.00030000:radio: IEEE standard IBSS ad-hoc mode supported
[   19.230937] airport 0.00030000:radio: WEP supported, 104-bit key
[   19.230948] airport 0.00030000:radio: WPA-PSK supported
/QUOTE]
for the second command
[QUOTE/lib/firmware/agere_ap_fw.bin  /lib/firmware/agere_sta_fw.bin/QUOTE]

---

### Post by canhoto on 2011-03-17
For "groups":
> adm dialout fax cdrom tape audio video plugdev fuse netdev lpadmin admin nopasswdlogin sambasha

---

### Post by rsavage on 2011-03-18
I'm not sure what is wrong to be honest.  Everything looks ok from what you've cut and pasted.  

Why didn't you try the first workaround since you are only using wep?  I'm guessing at the numbers here, but I think it is saying the airport card is flashed with v8.7 firmware.  If you wanted wpa (more secure) with network manager you would have to update the firmware from within mac os.

My guess about wicd not working is that network manager has not been fully uninstalled.  I don't understand why you did it through synaptic and didn't follow the instructions?  When you do it from the terminal it will give you some message about network-manager-gnome that it asks if you want to remove too.  You should reply yes to this.  Did you get this?  Also, did you try the second workaround?

I don't have a computer to test at the moment, so I'm going to hand this over to others.  WWeeks or Snafu006 both have airport classic and working wifi.  Try and find out what exactly they did and get them to document it.

---

