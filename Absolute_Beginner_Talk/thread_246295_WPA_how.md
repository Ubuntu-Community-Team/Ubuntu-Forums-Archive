---
title: "WPA how"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by manfredell on 2006-08-29
I installed Ubuntu 6 on my Dell laptop. Everything works fine.
Just one thing: when I try to connect my wlan card I only have option to enter WEP key. My router uses WPA.
Where and how can I connect my wlan card to a WPA router???


Thx a lot in advance.


Manfred

---

### Post by funchords on 2006-08-29
in many cases, all you have to do is 

apt-get install network-manager-gnome 

after it installs, reboot so that it can properly detect your wireless network card.  Double-click the icon (near the clock/system tray) to choose your network.  It will prompt you for your WPA key.

---

### Post by manfredell on 2006-08-29
You mean entering this in a terminal window?
There is already a wlan icon near the clock showing the connection but this does not help configuting WPA.

---

### Post by funchords on 2006-08-29
The current icon is probably the network monitor, which is not the same.  

Yes, type it in a terminal window...  except it should be 

sudo apt-get install network-manager-gnome 

(I forgot the sudo)

---

### Post by manfredell on 2006-08-29
Thanks. I'll try later today once I get home and revert.

---

### Post by thread on 2006-08-29
I'm also following along. After the reboot, though, I see "No network devices have been found" when I click on the nm-applet.

my rt2500 driver is loaded and recognizes the card. I've been using it with WEP just fine. I need to do WPA now.

---

### Post by thread on 2006-08-29
Ah! These instructions did it for me:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-af86b211b480d43b791cd9b4e698f96638d6d25f](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-af86b211b480d43b791cd9b4e698f96638d6d25f)

---

