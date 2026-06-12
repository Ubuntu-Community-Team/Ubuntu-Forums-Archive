---
title: "eee 901 has no wifi with 11.04"
date: 2011-06-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by KrashKit on 2011-06-12
I have a EEE 901 (the one with the 4gb/8gb drives). I am a complete newbee to Ubuntu and I also just can't get the wifi working.
 
It is on in the bios and the shortcut key appears to turn it off and on (function + F2). The wifi won't auto detect my router (which is WAP2 protected) or any of my neighbours routers which are unlocked. I have installed "wifi radar" and this does not locate any routers.
 
The driver list shows nothing and I do not know where to do from here short of going back to XP (which I don't want to do).
 
Any answers please try and write as if you were speaking to a five year old (this is closer to my mental age than my actual age :smile:
 
Thx for anyones time in advance.
KrashKit
 
P.S works fine but might as well use desktop PC for that.

---

### Post by webofunni on 2011-06-12
Are you able to see the wireless interface in ifconfig ?

---

### Post by KrashKit on 2011-06-12
No idea, can't find ifconfig?

---

### Post by webofunni on 2011-06-13
I am asking, if you are able to see that wireless interface in ifconfig or iwconfig. 

execute 

```

ifconfig
iwconfig 

```

---

### Post by Plumtreed on 2011-06-13
To the 5 year old....click on the tab with the scissors, go to accessories>click on 'terminal'

In the terminal type in these commands, cut and paste the result to your next post here.

This may give us an indication of what is required.

---

### Post by fishwilson on 2011-06-15
First of all: Is the blue light on? (The one with the wi-fi symbol over it besides the touchpad to the right), If not you may have to press Fn (key) + F2 to turn on wi-fi. If
this doesn't work you may have to take a little tour inside the bios settings by
pressing the F2 key at start up and enable wi-fi under 'onboard devices'.

---

### Post by finnbuntu on 2011-07-10
This seems to be a common problem with 11.04! Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1775041&page=2]("http://ubuntuforums.org/showthread.php?t=1775041&page=2")
Hope this helps,
Finnbuntu

---

