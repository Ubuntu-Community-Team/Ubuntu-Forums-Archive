---
title: "enabling WPA encryption"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by lena on 2007-04-09
Hello there,

I am so glad to have found the absolute beginners forum! I have been reading through material on WPA and Ubuntu and my head is spinning.

I recently installed Ubuntu and am trying to set up a wireless network. 
I am using an IBM T20 laptop and a Netgear WG511T wireless card. Our network at home is WPA encrypted and I don't know how to set this up in Ubuntu. 

Any help would be greatly appreciated!

Best,
lena

---

### Post by mand0 on 2007-04-09
Search in the Synaptic Package Manager for "WPA".  There's a specific package that handles that stuff. I can't be any more specific because I am on a Windows-only computer.

---

### Post by Sidhe on 2007-04-09
Not quite sure, since I tend to use WEP on my own network, but maybe this link is what you are looking for? :)

[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

Hope it helps.

-S.

---

### Post by dhughes on 2007-04-09
Install the package wpa-supplicant using Synaptic Package Manager and then look for any information you can find on it. Setting it up takes a few steps but it shouldn't be too hard, if I did I'm sure anyone can.

 **edit:** I see there is also a package called wpagui that may be useful, I set mine up using the command line, I wish I had known about wpagui at that time!

 If you don't know about it this is a good website to generate a long complex passwords:
 [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

 Good job for choosing WPA over WEP, it's much more secure. Recently (April/2007) I read an article about how WEP was broken in under a minute.

---

### Post by MacsRock on 2007-04-09
Follow this thread [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Works like a charm.

---

### Post by i.am.canadian on 2007-04-09
Hi there,

The easiest thing to do is to go to the terminal and enter ```
sudo aptitude install network-manager-gnome
```.

Once that is installed go to **system**, **preferences**, **sessions**.  Now go to the **startup programs** tab and click **+add**.  Enter the following: ```
nm-applet
```.  Now logout and log back in and you should have an icon in your tray, click on it and select your network SSID and then enter your password.  I hope that helps.

Cheers.

---

