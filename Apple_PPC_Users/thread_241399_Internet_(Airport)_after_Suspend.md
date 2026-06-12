---
title: "Internet (Airport) after Suspend"
date: 2006-08-22
forum: Apple PPC Users
---

### Post by smbrow14 on 2006-08-22
Suspend works fine with my iBook G4, but after resume Network Manager isn't able to connect to my wireless network. I found the solution in another thread, which was to:

```

sudo modprobe -r bcm43xx
sudo modprobe bcm43xx

```

This works fine but it's somewhat of a hastle. I found that /etc/power/scripts.d is where scripts to be executed before suspend and after resume are stored (with a symlink in /etc/power/event.d). I tried the following script but it doesn't seem to work:

```

#!/bin/sh

. pmcs-config

case "$1" in
  powersave)
    ;;
  custom)
    ;;
  performance)
    ;;
  suspend)
    sudo modprobe -r bcm43xx
    ;;
  resume)
    sudo modprobe -r bcm43xx
    sudo modprobe bcm43xx
    ;;
esac

```

I've also tried just doing:

```

#!/bin/sh

sudo modprobe -r bcm43xx
sudo modprobe bcm43xx

```

but that doesn't work either. This is my first attempt at shell scripting but I basically copied from the format of the other scripts in scripts.d. Any ideas on getting this to work properly?

---

### Post by rasec on 2006-08-22
I have a similar problem to yours on my powerbook. After I resume from suspend, network manager shows that it is still connected to the network, but its not. Network manager still works, but I have to manually reconnect to the network. Don't be surprised if it take sa little while to connect. It takes my computer about 30 seconds to connect to the access point.

About the power script, it looks fine, but I don't think it's relevant to powerpc based macs. X86 machines use ACPI to handle their power management, where as powerpc macs use a  proprietary PMU and that script written for the x86. I could be wrong though.

---

### Post by smbrow14 on 2006-08-23
I found the solution at [Lantern Torch]("http://www.lanterntorch.com/free-software/298/wireless-networking-just-got-a-whole-lot-easier/"). The script is supposed to be placed in /etc/apm/scripts.d, not /etc/power/scripts.d. I just downloaded the script on that page to /etc/apm/scripts.d and then symlinked it in /etc/apm/resume.d and /etc/apm/suspend.d. It works perfectly!

---

