---
title: "problems with Wlan"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Bart Ellebaut on 2007-04-10
Just installed Ubuntu, my fist Linux-experience!!

I did it on my laptop, but encountered a problem. Ubuntu 6.10 does'nt see my WLAN card ISL3886.

After a search I found this thread: [http://ubuntuforums.org/showthread.php?t=332857&highlight=ISL3886](http://ubuntuforums.org/showthread.php?t=332857&highlight=ISL3886)

At step 4 I installed NdisWrapper 1.9, that was the only one available, didn't find 1.8 in the searchresults.

At step 7 one before last sentence: Left click on the Network Monitor > In Name over type 'lo' with wlan0 > [Close]

I don't get a signal strenght, it keeps saying disconnected and can't find out why!

Anyone who can help a Linux-n00b???!!!

---

### Post by halitech on 2007-04-10
copy the output of

```
lspci -l
```

and paste it here, configuring your network if it's not seeing the card isn't going to do much good

---

### Post by Bart Ellebaut on 2007-04-11
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging

---

