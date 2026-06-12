---
title: "Modprobe ndiswrapper not working; wireless won't stop roaming"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-11-30
**EDIT:** Problem solved!

I'm a former Dapper user who just got Gutsy installed. Ndiswrapper took my driver just fine (neti2120 : driver installed, device (17FE:2120) present), sudo depmod -a went just fine with no error messages. sudo modprobe ndiswrapper didn't give me any errors in the terminal I set the command in, and it *seemed* to execute fine, but checking /var/log/messages gave me this:

```
:~$ tail /var/log/messages
Nov 29 23:14:39 ubuntu kernel: [ 2029.184000] ndiswrapper (set_infra_mode:197): getting operating mode to failed (C00000BB)
Nov 29 23:14:39 ubuntu kernel: [ 2029.184000] ndiswrapper (set_auth_mode:642): setting auth mode to 0 failed (C0010017)
Nov 29 23:14:39 ubuntu kernel: [ 2029.184000] ndiswrapper (set_encr_mode:673): setting encryption mode to 1 failed (C0010017)
Nov 29 23:14:39 ubuntu kernel: [ 2029.184000] ndiswrapper (set_essid:59): setting essid failed (C0010017)
Nov 29 23:14:40 ubuntu kernel: [ 2029.956000] ndiswrapper (iw_get_range:1388): getting bit rates failed: C00000BB
Nov 29 23:14:40 ubuntu kernel: [ 2029.956000] ndiswrapper (iw_get_network_type:304): getting network type failed: C00000BB
Nov 29 23:14:40 ubuntu kernel: [ 2029.956000] ndiswrapper (iw_get_freq:324): getting configuration failed (C00000BB)
Nov 29 23:14:40 ubuntu kernel: [ 2029.956000] ndiswrapper (get_encr_mode:690): getting encryption status failed (C00000BB)
Nov 29 23:14:40 ubuntu kernel: [ 2029.956000] ndiswrapper (iw_get_essid:174): getting essid failed (C00000BB)
Nov 29 23:14:40 ubuntu kernel: [ 2029.956000] ndiswrapper (iw_get_infra_mode:260): getting operating mode failed (C00000BB)
```

iwconfig gives me:

```
wlan0     Auto  Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Link Quality:100  Signal level:0  Noise level:160
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifup/down give me:

```
~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
```

In my Network specifications, I have a wireless connection option, but it's set to "Enable roaming". Whenever I go into its properties and change it either to static IP or DHCP, it'll accept my changes, then go right back to roaming as soon as I click OK; going back in and changing it *again* still doesn't stop it from switching back to roaming.

I have zero internet connection, as far as Firefox is concerned. I have yet to try pinging the router; it's next on my list of things to try.

Help?

**EDIT:** Change in the status of things. Check below.

**ETA2:** CPU's overloading now. Shut the laptop down, but I'm worried.

---

### Post by Halfling Rogue on 2007-11-30
Bump. For the record, I was following the instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Halfling Rogue on 2007-11-30
Bump.

---

### Post by Halfling Rogue on 2007-11-30
Bump.

---

### Post by Halfling Rogue on 2007-11-30
Right, so, my network is no longer constantly enabling roaming. Now it's constantly *disabling* my network, and won't let me enable it again. Ping doesn't return anything except for localhost, and wlan0 keeps showing up and disappearing from Network Tools over and over again. The configuration button in Network Tools for wlan0 is greyed out, and in the Network panel it says that wlan0 isn't configured. So how the heck do I configure it?

---

### Post by Halfling Rogue on 2007-11-30
CPU is overloading now, running (or trying to run) at over 100%, even though I'm not doing anything at all and have nothing open. Pretty sure that's not good, and I don't know what process to kill to take some of the load off.

---

### Post by Halfling Rogue on 2007-11-30
Nobody can help? I'm really worried about the amount of resources this is taking up. I want to stick with Gutsy, but if I can't work this out I'll have to switch back to Dapper; I really need this machine working.

---

### Post by monte48lowes on 2007-11-30
Did you compile ndiswrapper from source, or did you install from the repositories? I was able to use the repos for ndiswrapper. That might not work for you.

Mike

---

### Post by Halfling Rogue on 2007-12-01
Solved the problem!! Installed [the latest ndiswrapper]("http://sourceforge.net/project/showfiles.php?group_id=93482") and followed the instructions in the INSTALL file. Wireless now works fine!

---

### Post by monte48lowes on 2007-12-01
Nice job Halfling. Please edit the Thread title and add [Solved] to the end so others know it's solved. Good work mate.


MIke

---

