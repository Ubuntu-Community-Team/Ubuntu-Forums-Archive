---
title: "enable wireless in console (runlevel 3)"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by voidmatters on 2007-09-26
***Solved...***

My **X Server doesn't want to run**, probably because **I installed the ati-xxx**-driver as a package **via add/remove** ...shame on me [-(.

So, not being able to get from kdm to kde,
I wanted to remove that ati-package and then **remove/install the xorg-driver-fglrx** via apt-get.

Anyway, I don't seem to be able to [SIZE="4"]**enable  wireless in console mode**[/SIZE] ...without the use of knetworkmanager in kubuntu feisty.
Does anybody know the right command(s) to "run" wireless in "Ctrl+Alt+F2 mode"?

I can look at my wireless adapter **eth1** with **iwconfig** and see that there is no signal,
yet there seems to be no **enable/connect** option.

So trying to run **apt-get install** I only end up with an **unable to fetch some archives ...**

Does anyone with some advise?


NB: Is there a way to scroll up the console output?
...because quite often I feel like there is an awfull lot of text that I am missing ;-)

---

### Post by darc on 2007-09-26
Scrolling up in the console can be done with "shift+page up"

Try the following for starting up your wireless (assuming eth1 is your wireless):
ifconfig eth1 up
dhclient eth1 -d &


Let us know how that goes,
-darc

---

### Post by voidmatters on 2007-09-26
Thanks **darc** for the quick reply...

After running...
```
ifconfig eth1 up
```

and trying to...
```
dhclient eth1 -d &
```

I get 4 times some...
```
DHCPDISCOVER on eth1 to 255.255.255.255 ...
```
with different ports and intervals which concludes with...
```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I am trying to connect to an "unprotected" / "open" network and I do know the essid...

Any further suggestion(s)?

---

### Post by Henry Rayker on 2007-09-26
I believe you need
iwconfig eth1 essid YOURESSID

Do this after the ifconfig.

---

### Post by voidmatters on 2007-09-26
> **Henry Rayker said:**
> I believe you need
iwconfig eth1 essid YOURESSID

Do this after the ifconfig.

Hi Henry, I tried that before and now... again.
Unfortunately, that alone doesn't seem to work.

Is there any other **iwconfig** setting that might be of the essence here?

---

### Post by voidmatters on 2007-09-26
I just tried to fidle with my hardware button (on/off/on/off/...) and to set the following...
```
iwconfig eth1 key off
```
...and finally, it works!
Puh, linux is so much (timeconsuming) fun ;-)

So hopefully I will get X back up and running, but that is another story...

Just if someone else will need to start an wireless connection in the console in some remote future... for me it (probably) worked like this (with eth1 being the wireless connector on my machine):

```
ifconfig eth1 up
iwconfig eth1 essid YOURESSID key OFF
#and maybe also the following options...
iwconfig eth1 ap OFF rate AUTO mode AUTO
dhclient eth1 -d &
```

---

### Post by Henry Rayker on 2007-09-27
Huh....was your ESSID previously keyed? I can't think of another reason you'd need to tell it that it should not use the key.

---

