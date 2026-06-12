---
title: "Wi-Fi Issues"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by ModernTenshi04 on 2006-12-11
Okay, I've been running Ubuntu on an old Toshiba Tecra 8100 for several months now.  Ever since the initial install, using my wireless cards has never been an issue; it's always just found my network, connected, and happy times ensue.

A few nights ago, however, I decided to encrypt my network with WPA Personal using a TKIP algorithm (previously it was wide open to anyone).  I made the change in my router, and was able to get my Windows machine to connect just fine, as well as my Nintendo Wii.  I switched Wi-Fi PCMCIA cards to a Cisco Aironet 350 series (model AIR-PCM352), entered the passkey, and everything seemed to be working just fine.  However, within the last 24 hours or so, my connection to the Internet has been extremely sluggish, and several times the other night, the connection just cut out for a little while.  Then I restarted the Toshiba Ubuntu is installed on, and suddenly it won't connect on either the Cisco card, or my Lucent Technologies/Orinoco Silver, though the Orinoco card shouldn't be a surprise, since it appears to only support WEP, which is why when I encrypted my network with WAP I had to use the Cisco card.

I am at a complete loss as to how to correct this issue.  I know my networks SSID as well as the WPA passkey, and I know the router is configured correctly since my Windows machine and my Wii have no issues connecting.  After attempting to connect to a few open networks I've found in my neighborhood, but it won't connect to those either.  I don't know if I want to have it use eth1, eth0 or wifi0 or whatever (no idea what either of those are).

I'm running Ubuntu Edgy Eft 6.10, and the latest updates for my system, as far as I can tell.  I've listed the two Wi-Fi PCMCIA adapters I have on-hand, and can confirm that they've worked flawlessly with the system up until the last 24 to 36 hours.  My wireless router is a Linksys WRT54GS rev. 2.0 with the latest firmware.  I have also tried booting into one of the many Ubuntu 6.06 LTS discs I ordered a while back to see if I could get networking to play nicely in a live-CD session, but to no avail (either my network, or one of the open ones).

Any help or suggestions would be greatly appreciated.

---

### Post by Iarwain ben-adar on 2006-12-11
Hi,
i don't know much about WiFi,
but did you try connection-manager? (have a search on the forums here)

I have WPA2 and my wifi works great! 


Iarwain

---

### Post by ModernTenshi04 on 2006-12-11
No, I don't have connection-manager installed.  I downloaded it after finding it in a Google search, but it said it conflicted with network-manager, so I uninstalled network-manager, then tried to install connection-manager, and it STILL says there's a conflict with network-manager!  Now I can't reinstall network-manager to try and recreate what I did in the first place.

Dammit . . . .  ](*,) 

BTW, by downloaded it, I mean I did it on my Windows machine, and transferred it over via my USB drive.

---

### Post by Iarwain ben-adar on 2006-12-12
did you try this?
```
sudo aptitude purge network-manager
```

This deletes everything that was installed by network-manager..

And btw, to install connectioin-manager, you have to install these aswell:
- libwxgtk2.6-0
- python-wxgtk2.6
- wpasupplicant


Iarwain

---

### Post by PartisanEntity on 2006-12-12
You need wpa-supplicant in combination with network manager to access a wpa encrypted network. I followed this method to get Dapper to connect to my wpa encrypted home network:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

