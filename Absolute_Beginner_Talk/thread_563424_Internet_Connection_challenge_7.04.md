---
title: "Internet Connection challenge 7.04"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by AGadfly on 2007-09-30
I have followed the sequence [**- HERE  -**](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html) without success.  I get to the part where it says "3 Ensure Enable this connection is turned on." but don't find that.  The properties box shows "enable _roaming_"

I have connection to my LAN so the NIC is working.

Ubuntu 7.04 on own partition
Nextnet wireless modem to ISP tower 
SMC 4 port router
NIC connected to router.

I have set up static address and the computer with Ubuntu installed is 192.168.0.1 | gateway (router) is 192.168.0.10 - This works for me with XP pro but I so want to migrate to Ubuntu.

Any and all help would be appreciated.  I searched on the word "Roaming" before writing this post BTW and it seems to be a new net problem.

THX 
Gad

---

### Post by bobplano on 2007-09-30
i think you are a screen too deep. go to where is displays the three choices, wired, wireless, and modem, and make sure there is a check by the one you want

---

### Post by AGadfly on 2007-09-30
Thank you bob - but I'm still a little lost. I don't see three choices " wired, wireless, and modem,".

System>administration>network brings me to 'Network Settings' with a choice between Wired Connection  which is ticked; and Modem Connection which is unticked.  (I have used the DU modem for faxing in XP).

The modem connection refers to a dial up modem and I do not use it to connect to the net. I actually connect through Wired ethernet>SMS barrricade router>Wireless Broadband modem/antenna>Internet

The "settings for eth0" seem to be fine but the upper left box is labeled "Enable Roaming Mode".  Since I'm using a desktop I hope it won't start "roaming" on me :)  but am wondering whether my computer is being recognized as a laptop by Ubuntu for some reason.

I have ticked the "enable roaming mode" which graqys out all my static connections and still does not give me internet connection even though the network icon in the top bar of the screen says "you are now connected to the wired network".

I can see the rest of my LAN without ticking the "roaming" box.

Hope there's enough there to give you a clue what I'm missing.

Gad

---

### Post by AGadfly on 2007-09-30
I also ran ifconfig in a terminal window and where I think I should see the eth0 address as 192.168.0.1 somewhere in the listing it does not appear - although 127-0.0.1 appears in the 'lo' section.

Thx

---

### Post by wetland on 2007-09-30
Do you see your eth0 device listed at all?

If you see eth0 that is good. You could try to configure your static ip address by trying this [link.]("http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html")

You can use the command 
> 
sudo gedit /etc/network/interfaces

Instead of the vi.

---

### Post by AGadfly on 2007-10-01
> **wetland said:**
> Do you see your eth0 device listed at all?

Yes - it shows up in the interface file and also in "ifconfig"

When I open the ~/etc/network/interfaces  file the static address seems to be properly set although it is missing some lines as displayed in the "Geek" link.  When I try to add the missing lines I find I don't have permission and don't know how to edit as admin.

---

