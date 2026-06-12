---
title: "suspend and hibernation  problems"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-02-13
when my computer is changing mode to suspend or hibernation nothing responds i see a black screen and i have to unplug it...  
some help?

---

### Post by Thingymebob on 2008-02-14
Same issue on my laptop. I must admit I've given up recently trying to get it work. I've tried just about every suggestion in these forums uswsusp etc but still get the same blank screen with blinking cursor and only a hard reset gets me out.

---

### Post by someoneouthere on 2008-02-14
it used to work for me in the past.....but now no... maybe it's something with the updates...

---

### Post by emarkd on 2008-02-14
I can't help you with your problems, but maybe I can prevent you from making them worse.  A hard reset on a Linux box is a very bad idea.  The journaled file system really needs to be cleanly unmounted to prevent corruption.  If you're experiencing lockups, take the time to read and learn [this technique]("http://www.arsgeek.com/?p=787").  It could save you lots of future trouble.

---

### Post by someoneouthere on 2008-02-15
thnx i hope it will help

by the way on my last "zombie" session the log was:
```

...Feb 15 04:58:43 select-laptop last message repeated 12 times
Feb 15 04:59:23 select-laptop last message repeated 8 times
Feb 15 04:59:25 select-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Feb 15 04:59:25 select-laptop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Feb 15 04:59:25 select-laptop NetworkManager: <info>  Deactivating device eth0. 
Feb 15 04:59:25 select-laptop avahi-daemon[5932]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb 15 04:59:25 select-laptop avahi-daemon[5932]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Feb 15 04:59:26 select-laptop avahi-daemon[5932]: Withdrawing address record for fe80::203:dff:fe37:2089 on eth0.
Feb 15 04:59:26 select-laptop avahi-daemon[5932]: Withdrawing address record for 192.168.1.2 on eth0.
Feb 15 04:59:26 select-laptop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Feb 15 04:59:26 select-laptop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Feb 15 04:59:27 select-laptop NetworkManager: <debug> [1203044367.519428] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_03_0d_37_20_89'). 
Feb 15 04:59:27 select-laptop NetworkManager: <info>  Deactivating device eth0. 
Feb 15 04:59:28 select-laptop nufw[6069]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 15 04:59:29 select-laptop NetworkManager: <debug> [1203044369.469270] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_15_00_28_bf_0d'). 
Feb 15 04:59:29 select-laptop NetworkManager: <info>  Deactivating device eth1. 
Feb 15 04:59:29 select-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: No such device 
Feb 15 04:59:33 select-laptop nufw[6069]: AUDIT: rx=0 tx=0 track_size=0 list=empty
```

if anyone can help...

---

### Post by someoneouthere on 2008-02-17
bump

---

### Post by blumagic on 2008-02-19
I have found this link helpful in getting my laptops to suspend/hibernate successfully.
Of course, your mileage my vary, but this site does give you good insight into this problem.

[http://people.freedesktop.org/~hughsient/quirk/index.html](http://people.freedesktop.org/~hughsient/quirk/index.html)

Good Luck,

blu.....

---

### Post by ace007 on 2008-02-19
I likewise have exhausted the resources of these forum trying to get my laptop to suspend/hibernate/  But for all of you who read this thread, know that your problems may be solved easily by doing a fresh install of Feisty Fawn (7.04).  Gutsy is known to not play nice.  I installed feisty on my laptop, and now all those problems have vanished.  And its really not that big of a hassle to do a fresh install.

---

### Post by someoneouthere on 2008-02-28
i have nightmares about reinstalling again, it would be a huge loss of data... 
are there any commands to show me the status of this functions?

---

### Post by someoneouthere on 2008-02-28
at first everything was fine...

---

### Post by Thingymebob on 2008-02-29
> **blumagic said:**
> I have found this link helpful in getting my laptops to suspend/hibernate successfully.
Of course, your mileage my vary, but this site does give you good insight into this problem.

[http://people.freedesktop.org/~hughsient/quirk/index.html](http://people.freedesktop.org/~hughsient/quirk/index.html)

Good Luck,

blu.....

Thanks for that page, I'm going to give some of that a try.

---

### Post by michael.conner on 2008-02-29
Thanks for that link. My Xubuntu installation didn't have pm-utils automatically installed for some reason. Now my Acer (Aspire 5100) is working like it should.

---

