---
title: "Wireless card setup: Belkin FSD6020"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Sunships on 2007-03-11
Hi, I am new to Ubuntu, and am trying to get my wireless card to work.

So far I have followed the Ndiswrapper instructions described here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

ndiswrapper -l gives:

```
bel6020 driver installed, hardware present
```

but when I do  "sudo depmod -a" and "sudo modprobe ndiswrapper", followed by "tail /var/log/messages" I get this:

```
Mar 11 19:32:05 ubuntu1 gconfd (root-4570): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 11 19:32:05 ubuntu1 gconfd (root-4570): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 11 19:32:05 ubuntu1 gconfd (root-4570): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 19:32:05 ubuntu1 gconfd (root-4570): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 11 19:32:05 ubuntu1 gconfd (root-4570): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 19:32:35 ubuntu1 gconfd (root-4570): GConf server is not in use, shutting down.
Mar 11 19:32:35 ubuntu1 gconfd (root-4570): Exiting
Mar 11 19:39:36 ubuntu1 kernel: [17180337.048000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Mar 11 19:39:36 ubuntu1 loadndisdriver: loadndisdriver: load_all_devices(524): no valid drives found in /etc/ndiswrapper; you may need to reinstall Windows drivers 
Mar 11 19:43:32 ubuntu1 kernel: [17180572.968000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)

```
(Apologies, I'm sure there is more there than is actually required to diagnose the problem, but I didn't want to leave anything out, just in case!)

I have found this thread: [http://ubuntuforums.org/showthread.php?t=11485](http://ubuntuforums.org/showthread.php?t=11485)
but understand very little. I also checked the ndiswrapper list, which advised me to try a Realtek driver. This didn't work either. 

If anyone has any personal experience with this wireless card, or any advice it would be greatly appreciated. Thank you!

---

### Post by OldTimeTech on 2007-03-11
Go to Main Support on the Forums here and then to Network and Wireless.....I did a search on wireless cards before I answered this and seems that the connectivity for Edgy and Wireless are not all that good......but I would try the forum where someone might have an answer for you.

---

### Post by Sunships on 2007-03-11
Okies will do. Thank you!

---

