---
title: "No network (wired/wireless) Gutsy MacBook Pro C2D"
date: 2008-01-02
forum: Apple Intel Users
---

### Post by ethien on 2008-01-02
Hi everyone

Recently instralled Gutsy in a triple boot configuration on a MacBook Pro 15" Core 2 Duo 2.16 Ghz, as I would like to switch totally to Linux from OS X, but would like to do so gradually as Linux and its world is completely foreign to me.

Wired connection was working at first, and I used the MacBook Pro tutorial ([https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)) to install madwifi-ng. This seemed to work as I saw the wireless icon at the top of my screen with all local networks access points listed. I selected mine, entered the WPA password.

I could not get a connection so did another reboot. The wireless icon has now disappeared, and both wired and wireless connections lost.

I am trying to fish around for answers but I have limited amount of time everyday (I have a young child) and it's now been several days of fruitless search :(

Any pointers to start identifying what went wrong would be vastly appreciated! I can post output of commands if required (did not do so straight off the bat as I did not know which were of interest)

Cheers
ethien



[EDIT]
Forgot to add I have tried blacklisting ath_pci in /etc/modprobe.d/blacklist and adding it to /etc/modules as seen in another post. Also tried to "insert the driver into the running kernel (whatever that means!) as per instructions in the tutorial linked in the above. I have also tried to disable ath_hal in /etc/default/linux-restricted-modules-common as per instruction on the madwifi website.

---

### Post by cyberdork33 on 2008-01-03
> **ethien said:**
> Forgot to add I have tried blacklisting ath_pci in /etc/modprobe.d/blacklist and adding it to /etc/modules as seen in another post. Also tried to "insert the driver into the running kernel (whatever that means!) as per instructions in the tutorial linked in the above. I have also tried to disable ath_hal in /etc/default/linux-restricted-modules-common as per instruction on the madwifi website.

Do not add it to /etc/modprobe.d/blacklist as that will block ANY module named ath_pci, including your compiled one. Placing it in /etc/default/linux-restricted-modules-common will only prevent those modules provided in the linux-restricted-modules-common package (which includes an older version of the atheros drivers that you are trying to replace).

Either way, compiling madwifi should not change how your wired networking operates as it is unrelated, so this may not be the root of your problem.

---

### Post by ethien on 2008-01-03
I was only following instructions I found here and there for problems that seemed similar to mine!
Anyway I have since reverted all modified files to their original state to no apparent avail.

Sounds like I'm in for a re-install... arg

Thanks for the reply ;-)

---

