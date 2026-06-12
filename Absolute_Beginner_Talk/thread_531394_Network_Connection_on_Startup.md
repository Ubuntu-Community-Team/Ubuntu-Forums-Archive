---
title: "Network Connection on Startup"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Chadwick17 on 2007-08-21
Couple quick questions about Ubuntu and connecting to a network. When the loading screen is up, I have text enabled, it seems to take a long time to process network connections... is this normal? Not really a big deal, but lengthens the startup process.

Also, is there a way to disable needing a password for connecting to my wireless networ? Not the WEP key, but the user password for Ubuntu.

Thanks in advance!

---

### Post by PetePete on 2007-08-21
check your /etc/network/interfaces file
you might need to comment out some devices which you aren't using, eg eth02 etc

You should be able to put the WEP key inside that interfaces file and it will connect on boot up, 

```

auto ra0
#use your relievent device name, might not be ra0, maybe wlan0 
iface ra0 inet dhcp

wireless-essid EssidHere
wireless-key abcd--keyhere

```

---

