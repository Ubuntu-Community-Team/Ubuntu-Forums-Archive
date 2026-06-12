---
title: "need to keep reinputting network details"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by usugar on 2006-10-14
Hi,

New to this and have a couple of little queries (which I'm putting in seperate posts - hope this is OK)

Ubuntu has no problem connecting to my wireless router - however every time I restart the computer or bring it back from hibernation, the network stops operating and I have to use Network Settings - Properties then re-type either the SSID or the WEP key (they're already shown, I just have to re-type them!).  Then Ubuntu applies the "new" settings and everything works again.  This is not fatal of course but it's a bit of a pain, especially as I'm currently doing lots of updating, installing &c so am frequently restarting the system

Can anyone help?

thanks

---

### Post by steve.horsley on 2006-10-14
Once you have it working nicely, go to the network settings, click Location and Create Location. It will create a location that has the current settings. Then at least you can retrieve the settings quickly. I have no idea why it doesn't remember your settings on restart - it should.

---

### Post by usugar on 2006-10-20
> **steve.horsley said:**
> Once you have it working nicely, go to the network settings, click Location and Create Location. It will create a location that has the current settings. Then at least you can retrieve the settings quickly. I have no idea why it doesn't remember your settings on restart - it should.

Thanks for this tip Steve.  However, it turns out that reloading the saved location takes longer than re-typing the details (loading a saved location takes around 30 seconds, whereas it takes five seconds to re-type the SSID or passkey and another five to apply these "new" network settings.).

Anyone know of a start-up file I can fiddle with to force the settings to be applied without me having to re-type then every time?

cheers

---

### Post by ceb on 2007-01-15
I have this problem with Ubuntu 6.06 LTS. Has anyone solved it?

Thanks

---

### Post by Karl Norway on 2007-01-15
Do the same
It will work 
I had Ubuntu 6.06 LTS before I installed Edgy (6.10)

---

### Post by be_placid on 2007-01-15
> **steve.horsley said:**
> Once you have it working nicely, go to the network settings, click Location and Create Location. It will create a location that has the current settings. Then at least you can retrieve the settings quickly. I have no idea why it doesn't remember your settings on restart - it should.

I have found the Location feature of network-admin extremely unreliable and completely unusable - nothing is ever saved per location. I now just tend to edit /etc/network/interfaces manually.

---

### Post by ceb on 2007-01-15
Thanks for your replies.

*Regarding be_placid's response:*

I have already tried editing /etc/network/interfaces manually, and mine looks like this:

```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid private
```

I turn on my computer, log on, and I have the NetworkManager applet telling me there are no networking devices, and Network Monitor telling me that ath0 is idle. I can't access the Internet. 

If I open Network Settings, deactivate the Ethernet connection, deactivate and then activate the Wireless connection, then click on ok, after a pause everything works fine. 

Does anyone know how I might be confusing the system here?


*Regarding Karl Norway's response:*

I'm not sure if you were referring to the advice to setup a location. I have tried that, and I find it's no better than clicking deactivate and activate. Is it possible to force the location to be selected on startup or login, rather than having to select it myself each time?



Thanks again

---

### Post by ceb on 2007-01-22
Seems like lots of people might be having the same problem:
[http://ubuntuforums.org/showthread.php?t=322982&highlight=network+manager+save+settings](http://ubuntuforums.org/showthread.php?t=322982&highlight=network+manager+save+settings)
[http://ubuntuforums.org/showthread.php?t=268065&highlight=network+manager+save+settings](http://ubuntuforums.org/showthread.php?t=268065&highlight=network+manager+save+settings)

---

