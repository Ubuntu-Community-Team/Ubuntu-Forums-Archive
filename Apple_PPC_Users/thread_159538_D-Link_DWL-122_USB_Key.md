---
title: "D-Link DWL-122 USB Key"
date: 2006-04-13
forum: Apple PPC Users
---

### Post by hvaria on 2006-04-13
Hi,

I have a D-Link DWL-122 USB Key

My Network Information:
SSID: VARIA
Encryption: None
Mac Address Filter: On

Steps taken before inserting the key into the computer:
1) Install linux-wlan-ng
2) Create a file called wlancfg-VARIA by copying wlancfg-DEFAULT
3) Edited the wlan.conf file to replace SSID_wlan0="" to SSID_wlan0="VARIA"

After this I inserted the USB key but I do not have any internet. I tried iwconfig and it says no wireless networks for wlan0

I know the mac address filtering works because I use the same key with OS X and it works fine.

Any help is really apreciated since I have red a lot of posts and have no clue why this is not working.

hvaria

---

### Post by hvaria on 2006-04-13
Also my Channel is 11 and so I added 11 to the list of channels on the wlan.conf file

---

### Post by Fantastic Dan on 2006-04-17
I am in the same situation. Thanks for any help someone could provide.

---

### Post by CaKiwi on 2006-06-13
Someone else has posted about the same problem.

[http://ubuntuforums.org/showpost.php?p=465719&postcount=7](http://ubuntuforums.org/showpost.php?p=465719&postcount=7)

---

