---
title: "Wireless Won't Connect unless SSID Enabled"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by CDS4LD on 2007-05-02
Have installed and updated Ubuntu 7.04 and everything is running and connecting great except for my wireless card.  It is a D-Link DWL-G510 using an Atheros chipset.  If I enable SSID, the card sees the network, asks for my WPA password and connects right up, no problem.  If I disable SSID, the card sees the network (I suppose because of saving the settings) but will not connect properly (ie it does not receive an IP Address from the router).  Multiple reboots and the same thing happens.  Any thoughts on how to solve this are greatly appreciated.

---

### Post by Emerzen on 2007-05-02
Well, an indirect thought.  I used to not broadcast my SSID from my router (but it still connected to Linksys though).  However, I read an article in PCWorld about wireless security.  It actually recommended not disabling the broadcast.  The reasoning was as follows:
-if your network is encrypted with WPA, your random neighbor's not going to be able to get in
-a real hacker will have no problem finding your network whether SSID is broadcast or not (the WPA or better WPA2 is still likely to prevent intrusion)
-so, disabling the broadcast causes you, the user, a minor-moderate hassle and is irrelevant to a hacker, so why cause yourself the trouble?

So, I broadcast now (w/WPA) and haven't had any intrusions...food for thought.

---

### Post by b1g4L on 2007-05-02
YES! I am experiencing the same issue with Feisty. I didn't have this with previous releases of Ubuntu. I'm assuming it's a bug, because it should still connect whether SSID is broadcast or not. I'll try and find out if a bug report has been submitted about this issue.

---

### Post by mspacek on 2007-05-03
I can confirm that i have the same problem. Punching in the SSID, choosing WPA, and entering the passphrase in the network config applet in the system tray (or whatever it's called) would send it off looking for the network, but never connecting. Enabling SSID broadcast on my WPA wireless router resolved this, and now wireless works great.

This was Feisty on a Thinkpad T41 with an Atheros 5004g internal mini PCI card.

Martin

---

### Post by b1g4L on 2007-05-03
I looked and there are multiple bug reports regarding this issue. They may release a fix sometime in the future - until then I'll just use wireless MAC filtering and WPA.

---

### Post by CDS4LD on 2007-05-03
Thanks for the responses...Hadn't thought about searching through the bug reports...Glad to hear it probably isn't something I'm doing wrong!

---

### Post by johntelthorst on 2007-05-10
I have the same problem, at home were I can control the router I just turned on SSID broadcasting, but at other venues where the SSID is not broadcasted, I have to go back to using WPA Supplicant.

---

