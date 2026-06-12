---
title: "Intermittent Wifi Issue BT5"
date: 2013-11-05
forum: Any Other OS
---

### Post by albgk on 2013-11-05
Hi friends,

I am fairly new to linux and am attempting to start using backtrack 5 for some penetration testing on my home network. This being said, after I installed backtrack 5 I have been having wifi issues. The I can connect to my network but within a minute or two I can no longer load any pages. 

It seems to be similar to this: [http://www.backtrack-linux.org/forums/showthread.php?t=40352](http://www.backtrack-linux.org/forums/showthread.php?t=40352)   I have tried all of the suggestions on this page with no avail. 

I have attempted to uninstall wicd and try network manager, but this did not seem to work. (I may have messed something up with this one). I should note that if possible I would like to use wicd, but am not married to it.

I have also attempted to connect manually using the following:
```
iwconfig wlan0 essid yadada
iwconfig wlan0 key s:yadada

```

I get an error like the following:
```

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```

Other useful info. When I connect through wicd, once it stops working and is endlessly trying to load a page, the internet to all devices on that network is affected (my phone starts to say the connection is unstable). 

Also, I am running this on a secondary hard drive that I have in the computer I am currently writing from. 
The specs are as follows:
Intel Core i5-2300
8gb ram
NVIDIA GeForce GTX 560
Main OS- windows 7 on SSD
Secondary OS- Backtrack 5 rel 1 KDE 32bit on HDD with 100gb partition

If anyone could please lend some help that would be much appreciated. As I said before I am new so if you request any further info (which I will attempt to fulfill in a timely manner) please elaborate on how to obtain that info. Same apply's to any methods to potentially fix this issue.

Thanks in advance,

Austin

---

### Post by albgk on 2013-11-10
Hi everyone,

I just wanted to give an update... I started over and am now using Backtrack 5 r3 KDE 64bit... The wicd manager started after reconfiguring and updating the defaults files. It went for approximately 5 minutes and then disconnected. Afterwards I could not get any internet. 

Please let me know if you have any suggestions, as this is quite annoying.

Unrelated issue: with r3 it has a menu after the motherboard posting screen that lets you pick which OS to boot with. How do I change which one is selected by default?

Thanks,

Austin

---

