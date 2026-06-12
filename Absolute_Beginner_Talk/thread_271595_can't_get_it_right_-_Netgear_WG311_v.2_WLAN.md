---
title: "can't get it right - Netgear WG311 v.2 WLAN"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by bdann on 2006-10-04
I'm having a difficult time with this:

System > Network Settings
I see "Wireless connection The interface wlan0 is active"
I click properties > enter my SSID.  I leave the WEP key black (I turned off WEP on my router).  Configuration is DHCP.
I click OK.
"Activating Interface wlan0"....for 40 - 60 seconds.
I click OK.
Again, "hourglass" for several seconds, then the window goes away.

At this point it does not appear that there is any network connection.

An ifconfig shows wlan0, but does not show a network address.

iwconfig shows the card, but it's not associated to my access point.

HELP!

What am I missing?  It seems dapper is recognizing the card out of the box, but it will NOT associated to my access point.  I've turned off all security on the access point and made the SSID the only the required to connect.

I've also tried to go the NDIS route installing the xp driver for my card....It shows the hardware is installed....but it no work!

Any advice is much appreciated.  I'm not ready to give up on ubuntu yet.

---

### Post by bdann on 2006-10-05
anyone? (bump)

---

### Post by deadgobby on 2006-10-05
[https://help.ubuntu.com/community/WifiDocs/WLANHowTo](https://help.ubuntu.com/community/WifiDocs/WLANHowTo)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wlan&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wlan&titlesearch=Titles)

---

### Post by bdann on 2006-10-05
I've read those, and it says it should work out of the box.  This is not helpful, b/c it doesn't work.

It also says if it takes a long time to activate the network then your encryption key is wrong.  Well, I turned WEP off, so there is no key.

I guess I'll bite the bullet and run a cable into the room with my ubuntu box.  This sucks.

---

### Post by bdann on 2006-10-05
Hole drilled, wire run. ](*,)

---

### Post by gn2 on 2006-10-05
Did you allow the wireless adapter's MAC address in the router's allowed list?

Was the adapter fitted and configured by the installer during install?

If not it can be almost impossible to get it running after install completed.
This happened to me and it took about six goes to get it right during the install phase. Just wouldn't work otherwise...

---

### Post by bdann on 2006-10-05
I turned off all mac address filtering....but before, yes, I had my wlan card's MAC address in the filter list.

Yes, the card was installed at the time Ubuntu was installed (if that's what you're asking).

Now that I've got the wired connection up, everything is great.  I'll probably give the wlan card another go after I've got everything else configured how I like.

---

### Post by apoth on 2006-10-08
Stick something like ```
options acx firmware_ver=1.2.0.30 
``` in /etc/modprobe.d/options

---

