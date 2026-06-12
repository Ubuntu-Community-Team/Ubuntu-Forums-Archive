---
title: "wifi trouble"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by bluebaby on 2008-03-06
i have a linksys wpc11 version 3 as my wireless network adapter. the network manager seems to recognize it and manages to find wireless networks available. when i try to connect to the network however it prompts me for a wep passphrase/key. i know that our network is operating with wpa encryption but networkmanager insists on wep. i still cant connect using wifi.can someone please tell me what&#347; wrong and how to fix it?

---

### Post by mikeyphi on 2008-03-06
> **bluebaby said:**
> i have a linksys wpc11 version 3 as my wireless network adapter. the network manager seems to recognize it and manages to find wireless networks available. when i try to connect to the network however it prompts me for a wep passphrase/key. i know that our network is operating with wpa encryption but networkmanager insists on wep. i still cant connect using wifi.can someone please tell me what&#347; wrong and how to fix it?

When you open System/Administration/Network  and select wireless/Properties - you should see, on the drop-down menu, two WEP and two WPA choices.
Do you not have these?
Also please say which version of Ubuntu you are using.

---

### Post by bluebaby on 2008-03-06
i am now trying kubuntu 7.10. i think i see  these choices but when i select a network it insists that it is on wep.

---

### Post by mikeyphi on 2008-03-06
> **bluebaby said:**
> i am now trying kubuntu 7.10. i think i see  these choices but when i select a network it insists that it is on wep.

After you have selected the network ESSID (name) you should still have the WEP / WPA choices in the 'password type' box.
Please confirm if this is not true on your system.

---

### Post by bluebaby on 2008-03-06
no. the choices in the dropdown box are wep hexadecimal and ascii  only.

---

### Post by mikeyphi on 2008-03-06
The next suggestion is to open Add/Remove and install Wifi Radar. See what that provides!

---

### Post by lswest on 2008-03-06
or you can install wicd, which has WPA support from: [http://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=ovh&filename=wicd_1.4.2-1-all.deb&13711178](http://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=ovh&filename=wicd_1.4.2-1-all.deb&13711178)

---

### Post by bluebaby on 2008-03-12
using wicd and wifi radar gave the same result. i'm now guessing that this is a driver problem. i will try to replace orinoco with hostap driver though i'm not sure how to do this.

---

