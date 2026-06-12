---
title: "KZenExplorer"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by gdboling on 2006-04-30
I have a Zen Sleep Photo.  I installed KZenExplorer without any problems.  Plugged the device into the USB port and turned it run. Ran KZenExplorer and it says it can't find any Jukeboxes.  KZenExplorer has no documentation on their website and the --help-all command doesn't give any hints as to what I might need to do to A) Specify a USB port or anything else.

When I plug the device in I get the following on dmesg

usb 5-3: new high speed USB device using ehci_hcd and address 5

Any help is appreciated.

---

### Post by MartinJ on 2006-04-30
Hi,

Have you tried running kzenexplorer as root.  I remember a post suggesting that and it seemed to work for some people.

Unfortunately, if your player has been upgraded to firmware version 2.x (PlaysForSure) it causes major problems.  More info on the library's page: [http://libnjb.sourceforge.net](http://libnjb.sourceforge.net)

There's an old thread here which might be of some use: [http://ubuntuforums.org/showthread.php?t=33040](http://ubuntuforums.org/showthread.php?t=33040)
Although it's for gnomad2, at least it's a start.

---

