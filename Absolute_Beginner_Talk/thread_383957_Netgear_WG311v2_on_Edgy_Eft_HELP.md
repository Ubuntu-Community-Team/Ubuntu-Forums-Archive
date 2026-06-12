---
title: "Netgear WG311v2 on Edgy Eft HELP"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Mohammad_Khalid_Hussain on 2007-03-13
Hi there,

I am a completely new Ubuntu(6.10) user(only used it for 2 days). Wanted to try Beryl. :P
Now the first thing i did was to install beryl which after a lot of research finally got to install the Nvidia proprietary drivers and all was okay.

Now my next problem is to be able to fix my Wi-Fi Card which is a PCI Netgear WG311v2. This card is recognized in Administration>Networking. It appears as wlan0. I have tried so many things just to get it connected to my wireless network.

I have tried:
1) Ndiswrapper until i found out my card has native support.
2) Network Manager but it doesnt really seem to help
3) Configuring it manually from the networking options. But it doesnt seem to have WPA options so i'm stuck again.

My Router is Linksys WRT54GL running DD-WRT frimware and wireless security is set to WPA-Pre Shared Key.

Other Information:
1)When Ubuntu is installed, the light of my WiFi card is ON and NOT OFF.
2)It is recognized as wlan0, It knows its there.
3)My wireless nework is using WPA-Pre Shared Key.

Now can someone PLS guide me STEP by STEP through the process of getting this fixed. Explain thoroughly stuff like "comment out"(which i didnt know what it meant till today) or how to edit read-only files whose attrobutes cannot be changed(which i had to figure out referring to different guides).

[COLOR="Blue"]EDIT: This problem has ben resolved by using WEP instead of WPA on my router. Thanx for all the help :)[/COLOR]

---

### Post by peabody on 2007-03-13
I know this isn't everything you asked for, but maybe this'll help.  To my knowledge, stuff for WPA support isn't installed per default, I think you need additional wpa packages for that, though I could be wrong (I think that was the case in dapper, I haven't looked into the default install of Edgy or Fiesty).

I'd first disable security on the router just to make sure the card can actually talk to it, then re-enable it and search for wpa on the wiki.

---

### Post by Mohammad_Khalid_Hussain on 2007-03-13
I will give that a try later and see if it works. One other thing, if i use WEP instead of WPA, there shouldnt be a problem then right?

---

### Post by peabody on 2007-03-14
In theory, I haven't heard of WEP being an issue among supported cards.

---

### Post by Mohammad_Khalid_Hussain on 2007-03-14
Hey it works when i disable WPA.
Then i tried to do something about WPA and ended up with Ubuntu not starting up.

Will try again after reinstalling it.

---

### Post by Mohammad_Khalid_Hussain on 2007-03-16
Okay, I fixed my problem by using WEP instead of WPA, I suppose i'll just wait for newer versions to make WPA easier for me ...

Thanx for helping :)

---

