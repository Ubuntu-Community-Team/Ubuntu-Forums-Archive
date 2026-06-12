---
title: "NetworkManager and Airport Extreme:  SUCCESS."
date: 2006-07-08
forum: Apple PPC Users
---

### Post by AlphaMack on 2006-07-08
I'm posting this from my 15" Al PowerBook using NetworkManager.  After struggling since Dapper Flight 5 to get the AirPort Extreme card fully working and functional, I finally stumbled on the solution as pointed out in the wiki for Broadcom-equipped cards and Dapper.

Once you have your firmware extracted and copied into /lib/firmware, make sure of the following:

(A) You have (K)NetworkManager installed.
(B) Wifi-Radar is **completely** removed from your system.  Apparently I didn't do this and it is supposedly conflicts with the bcm43xx driver.
(C) You disabled wpasupplicant.
(D) In /etc/network/interfaces everything is commented out except for lo.
(E) You modprobed bcm43xx.

```
sudo modprobe bcm43xx
```

Once you have done all of this, immediately reboot.

Upon logging back in, you should be able to see a menu of wireless networks from the nm-applet.  Select yours and be sure of the following:

(A) If using WEP, select 64/128 ASCII.
(B) Do not prefix your key with "s:".  It is not necessary.

Now connect and enter your keychain password when prompted.  If the first "LED" lights green, it's a good sign.  If the second then lights up, you're in!

Note you'll need to repeat the wireless network password entry process for each user (and saved to their keychains).

And yes, you'll even be reconnected after you wake the machine from sleep. :cool:

---

### Post by zachws on 2006-07-08
Any luck with this on an iBook?

---

### Post by rasec on 2006-07-08
I got network manager working with my powerbook too a while ago, but I had to recompile libmn-util0 to get it to work with WPA passphrases. I emailed the fix to Scott, the network manager package maintainer, so hopefully he'll include it in the next release of network manager.

Wow, your network manager reconnects you automatically after you resume from sleep? Must be a WEP thing. I have to reconnect to my AP manually.

---

### Post by AlphaMack on 2006-07-08
> **zachws said:**
> Any luck with this on an iBook?

It should work provided you try the steps as described.  I forgot to mention that you must also broadcast your ESSID.  I don't have much luck with closed networks right now.  Maybe I'll figure it out.


BTW, my base station is also an AirPort Express, so I was really surprised that I was able to get my connection to work 100%.

---

### Post by AlphaMack on 2006-08-04
> **rasec said:**
> 
Wow, your network manager reconnects you automatically after you resume from sleep? Must be a WEP thing. I have to reconnect to my AP manually.

There is a catch:  it attempts to reconnect to your previously selected base station...so if you sleep the computer and move it somewhere else, NM will try to find the station you were connected to.  It's easy to work around though; just select your base station of choice and NM will connect to the new station. :)

---

### Post by rasec on 2006-08-04
The thing is, when I resume from standby, NM thinks its still connected to the network but when I try open a web page it can't find the host. Most of the time I don't even move my laptop either, so it should work. 

On a side note, I managed to get my wpa issued resolved my emailing the debian maintainers the fix. I emailed the ubuntu maintainers and posted a bug report over at launchpad.net but I never received a response in over 2 months. It seems like the ubuntu devs just recompile the debian packages for the most part anyways, so hopefully the fix will eventually trickle down to ubuntu.

---

### Post by clebio on 2006-08-14
Can you explain how to disable wpasupplicant?

---

### Post by penguinzrool on 2006-12-24
All looks good until after I put in the key, then it just sits there with no green LED... dmesg reports:

[  304.872640] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  307.233221] SoftMAC: Open Authentication with 00:14:6c:16:ba:9b failed, error code: 13

so it looks like the AP's rejecting the key for whatever reason. Do you need to put the key in with dashes between the characters, or is one long string ok?

Cheers,
Chris.

---

### Post by atomik on 2006-12-27
Seems that NetworkManager not be able to put eth1 up..

In my test, if i reboot the machine, or switch network manager to wired network then modprobe -r bcm43xx and then modprobe bcm43xx, now trying to join wireless network work..

---

### Post by gamgee911 on 2007-01-06
ok I know this may be a stupid question but i'm a little new to linux.  When you say "In /etc/network/interfaces everything is commented out except for lo"  do you mean to put "# " in front of everything except
"auto lo
iface lo inet loopback" ?  Thank you.

---

