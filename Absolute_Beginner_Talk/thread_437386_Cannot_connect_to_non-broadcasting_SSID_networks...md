---
title: "Cannot connect to non-broadcasting SSID networks..."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Linux_n00b on 2007-05-08
I have a Netgear WG511T wireless card.  It seems that I cannot connect to my wireless network unless I turn on the option to "Broadcast SSID" in my router.  Could their be a possible way to connect to my network without  enabling broadcast SSID? Thanks!

---

### Post by bobplano on 2007-05-08
have you tried just putting in your (e?)ssid into the networking window? if you have wep you might try disabling that and then connecting your computer to the network. then try adding it back on

---

### Post by conjur3r on 2007-05-09
I have the exact same problem and it really drives me mad to have something that worked flawlessly in Edgy and previous versions (not to mention other distros), to end up with something inoperable after installing the latest feisty.  I'll do my best to make sure the people dealing with it for gutsy will fix it so that it once again works as expected.

---

### Post by johntelthorst on 2007-05-10
> **conjur3r said:**
> I have the exact same problem and it really drives me mad to have something that worked flawlessly in Edgy and previous versions (not to mention other distros), to end up with something inoperable after installing the latest feisty.  I'll do my best to make sure the people dealing with it for gutsy will fix it so that it once again works as expected.

Why wait till gutsy, can't someone patch it?  It is a shame it doesn't work, if not for this problem, I'd say the networking in Ubuntu is as good as OS X.  Now I have to go back to WPA Supplicant and the command line...

---

### Post by Linux_n00b on 2007-05-10
How can we get this patched?  I'm going to be pretty upset if the same problem happens in Gutsy......

---

### Post by Village on 2007-05-12
I seem to be having the same problem, connection works fine when the SSID is being broadcast, however when I turn it off it stops. This used to work in 6.10. 

Any suggestions welcome.

Village

---

### Post by surgenet on 2007-12-07
Has anyone had any luck with this? I've noticed that if I turn on SSID broadcast so Ubuntu (7.10) can see it and connect, then turn broadcast back off it works fine (until I reboot). It's like someone forgot to put the code in the Wi-Fi app to &#8220;look&#8221; for the SSID as well as to listen for it. Is there something I can add to the networking config file to force a search for the SSID (other then wpa-ssid <your essid>)?

---

### Post by HDave on 2007-12-08
I too had problems with this.  After some research I found it is a bug that has already been reported and is being worked.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214")

There were a few work-arounds discussed in the thread...I didn't bother to try them as they looked complicated.

Will wait for a patch....

---

### Post by surgenet on 2007-12-15
Glad to hear they are working on it. Thanks.

---

