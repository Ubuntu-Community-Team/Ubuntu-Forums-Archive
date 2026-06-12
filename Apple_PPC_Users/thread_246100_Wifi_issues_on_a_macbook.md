---
title: "Wifi issues on a macbook"
date: 2006-08-28
forum: Apple PPC Users
---

### Post by rkritzer on 2006-08-28
So I've successfully installed Ubuntu on my new macbook (the low-end model), and I just can't seem to get Wifi to work. So far I've:

  installed network-manager and network-manager-gnome

  run modprobe new_wlan_scan_sta and the other _ccmp and _tkip (so basically I got the madwifi and madwifi-ng drivers)

  downloaded wlassistant to make the connection easier

So wlassistant was able to scan for available connections. It found my connection just fine, but I still wasn't able to connect to it, while another laptop using wireless was able to connect. ](*,) 

I'm fresh out of ideas. Any help would be greatly appreciated. Thanks.

---

### Post by hajk on 2006-08-29
I know your frustration, been through those steps myself, and all to no avail. The problem is IMHO in the new madwifi-ng drivers, so a solution will just have to wait until upstream releases a new version. It must be these drivers, because iwconfig shows a signal strength of only 54/94 even when I'm positioned next to the base station. I have filed a bug on it, but don't hold your breath...

Meanwhile, the following procedure works if followed exactly (don't ask me why):

1. After booting, open System-Administration-Networking menu and first deactivate the ath0 interface, and then activate it again. (Assuming Properties configured, need to do that only once). Activation will take a long time, just let it run its course, and finally it will activate and the gateway shown will be ath0.

2. Leave the menu, open a terminal and check with "ping -c 4 www.yahoo.com" that the interface is in fact not up. But now give the command 
"sudo ifup ath0", and after the second DHCP request or so the interface will be up (as you can again check by pinging).

It's a pain having to do this everytime you boot, but at least the connection then works.

Good luck!

---

### Post by phersotty on 2006-09-03
I've been having the same problem for weeks even reinstalled from scratch thinking I missed a step.  I just now followed your instructions and when I got to the part about pinging in the terminal I got a response from yahoo!  I didn't need to sudo ifup ath0.

You said you have to do this every time you boot.  Isn't there a way to edit the boot process to do it automatically like through fstab or something?  

I'm really glad this worked even if I have to do it each time I reboot because now I can finally show off my Triple Boot Macbook=D>

---

### Post by hajk on 2006-09-04
I'm glad it works for you! I could never get it to work properly on my MacBook, so I have switched to using Ubuntu in a Parallels VM.

---

### Post by RelativelyQuantum on 2007-12-31
I'm trying to interface Gutsy with my MacBook Intel Core 2 Duo wireless hardware. *_I can't do it._* Does anyone have anything for me? I've followed these instructions exactly:

[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

To *_absolutely no avail._*

It obviously can be done. I just have no idea how ](*,)

If anyone has any information, or has experienced this problem, please post.

Thanks so much in advance.

---

