---
title: "Problem with Update Manager - 'report this bug...'"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by jannen on 2007-11-23
Need help: When trying to download and install updates in Ubuntu, I get this error message:

[B]"Could not initialise the package information
An unresolvable problem occurred while initialising the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:The package bcm43xx-firmware needs to be reinstalled, but I can't find an archive for it.'[/B]"


Its possible due to my thousands of trials to get the BT- laptop card working. However I swithced to a Belkin G USB stick which worked out of the box. But due to the above error I cannot install any updates... suggestions?!?

Thanks:confused:

---

### Post by Pumalite on 2007-11-23
Try:
sudo dpkg --remove --force-remove-reinstreq <packagename
sudo apt-get update
sudo apt-get upgrade

---

### Post by jannen on 2007-11-23
**Hi & Thanks. I still have problems with these commands.**

*sudo dpkg --remove --force-remove-reinstreq <packagename*
Do I here put 'bcm43xx-firmware' where you say <packagename?

*sudo apt-get update*
I get these errors:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

*sudo apt-get upgrade*
I get these errors:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Pumalite on 2007-11-23
That's your packaname it seems.

---

### Post by Partyboi2 on 2007-11-23
> **jannen said:**
> 

*sudo apt-get upgrade*
I get these errors:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


That happens when synaptic or another package update  installation application is already running. Close any other package managers (including Add/Remove, synaptic package manager.) and retry

---

### Post by jannen on 2007-11-24
Got it finally... thanks. Problem was I tried it with the < sign. Got the updates working finally.

And whats best... WIreless is working finally on Ubuntu!!! I was already looking to go back (and pay £££) for Windows... but will give Linux another shot. Yeah!

---

### Post by Pumalite on 2007-11-24
Good luck.

---

