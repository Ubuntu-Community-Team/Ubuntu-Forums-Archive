---
title: "Help identify onboard video chip!"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-11-21
Im helping a friend install Xubuntu on his old compaq pc. I don't know what model it is but I'm sure its far out obsolete. 

Is there a command to find out what kind of onboard video this thing uses (or video in general)? Thanks :D

---

### Post by bodhi.zazen on 2006-11-21
Hi WalmartSniperLX :p

Try ```
lspci | grep VGA
```

8)

---

### Post by WalmartSniperLX on 2006-11-21
> **bodhi.zazen said:**
> Hi WalmartSniperLX :p

Try ```
lspci | grep VGA
```

8)

Hi bodhi.zazen!

Thanks that worked

```

$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

```

EDIT: I searched ATI's site for drivers. I dont think theres linux support for this chip :S

---

### Post by steveneddy on 2006-11-26
Or even 
> 
lspci -X


That command actually got me the correct info I needed for xorg.conf.

---

### Post by bodhi.zazen on 2006-11-26
> **steveneddy said:**
> Or even 


That command actually got me the correct info I needed for xorg.conf.

???> **sudo lspci -X**
Password:
lspci: invalid option -- X
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
-i <file>       Use specified ID database instead of /usr/share/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging

---

