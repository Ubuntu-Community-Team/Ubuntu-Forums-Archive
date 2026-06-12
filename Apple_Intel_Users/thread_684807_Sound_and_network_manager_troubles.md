---
title: "Sound and network manager troubles"
date: 2008-02-01
forum: Apple Intel Users
---

### Post by wahr on 2008-02-01
While this _[documentation](https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d)_ has been very helpful to me, I've run into issues on the kubuntu side that don't respond to the ubuntu solutions. 

Outstanding in this regard is the sound (the exact problems detailed in the link), which has not responded at all to the measures suggested. 

The other issue is the Knetworkmanager tool, which is apparently not connecting with networkmanager, It's in the system tray, but the thing doesn't register the state of any of the network devices. I haven't the foggiest idea what's up and what's not unless I keep system settings open.  [that is if networkmanager is working properly itself. (I find myself manually refreshing the network connections...... could use a term command for it but haven't dug one up yet]


I look forward to any input on this.  Many thanks :)

---

### Post by cyberdork33 on 2008-02-02
Which macbook do you have? You might try looking here if you have one of the newest Santa Rosa Macbooks:
[http://ubuntuforums.org/showthread.php?t=610375](http://ubuntuforums.org/showthread.php?t=610375)

---

### Post by wahr on 2008-02-02
nope, not santa-rosa, its a plain old first gen 1.8 core duo

---

### Post by cyberdork33 on 2008-02-03
well then the drivers in the repos should be working for your hardware. you need to make sure the adapter is in roaming mode for network-manager to use it (in System > Administration > Network).

---

