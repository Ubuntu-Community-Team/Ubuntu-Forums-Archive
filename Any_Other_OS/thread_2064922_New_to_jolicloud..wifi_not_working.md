---
title: "New to jolicloud..wifi not working"
date: 2012-09-30
forum: Any Other OS
---

### Post by chucktwinlinton on 2012-09-30
Any help appreciated...

Installed today dual mode windows xp and Jolicloud 1.2 version. Note does not give me option go into windows during bootup, goes straight to Joliclound, but that is not a concern at this point. At this point just trying to make the Wifi work, working fine on xp before installing Jolicloud.

 Version Joli Cloud 1.2
  laptop: Gateway Model MX6123
  Modem internal  Broadcom 802.11g
  

Wifi is enabled but not show Wifi as active


Joli cloud suggestions and my reply:

  
[LIST=1]
[*][FONT=&quot]Open a terminal by pressing [/FONT][COLOR=white][FONT=&quot]Alt[/FONT][/COLOR][FONT=&quot] + [/FONT][COLOR=white][FONT=&quot]F1[/FONT][/COLOR][FONT=&quot] ([[COLOR=blue]more details[/COLOR]]("http://help.jolicloud.com/entries/231106"))[/FONT]
[*][FONT=&quot]Type: *sudo lspci -v -nn > lspci* (it      returns the list of your PCI devices - if your Wifi is built-in)[/FONT]
[/LIST]
  [FONT=&quot]I did above via copy and paste but the reply was:  
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot][sudo] password for pachanga10:[/FONT]
  
[LIST=1]
[*][FONT=&quot]Type: *ifconfig -a > ifconfig* (it returns      the list of network interfaces, the wireless interface should be wlan0 or      eth1)[/FONT]
[/LIST]
  [FONT=&quot]I did this [/FONT][FONT=&quot][FONT=&quot]via copy and paste [/FONT]and reply was: 
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]pachanga10@jolicloud:~$[/FONT]
  
[LIST=1]
[*][FONT=&quot]Type: *sudo iwlist wireless-interface-name scan >      iwlist* (wireless-interface-name should be wlan0 or eth1, it      returns the list of available wireless networks)[/FONT]
[/LIST]
  [FONT=&quot]I did above [/FONT][FONT=&quot][FONT=&quot]via copy and paste [/FONT]but the reply was:  
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot][sudo] password for pachanga10:[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]Finally, you can open the file system, go to */var/log* and retrieve the *dmesg* file.[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]I don’t understand how to do this.[/FONT]


[FONT=&quot]Any help appreciated. Thank you.
[/FONT]

---

### Post by Toz on 2012-09-30
Moved to Other OS/Distro Talk.

---

