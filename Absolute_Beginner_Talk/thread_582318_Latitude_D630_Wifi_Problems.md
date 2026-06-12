---
title: "Latitude D630 Wifi Problems"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Shyper on 2007-10-19
Hey everyone...

I just got a new Latitude D630 today, and installed Ubuntu on it. Alas, there was no sound, so I followed the instructions for getting sound working on this page:

[http://ubuntuforums.org/showthread.php?t=573330&highlight=d630+wifi](http://ubuntuforums.org/showthread.php?t=573330&highlight=d630+wifi)

The sound now works, but my wifi and ethernet is now totally shot. I can't get either to work, and have no Internet connection at all on the laptop. When I try to go to the Restricted Drivers manager on it, it says I need "linux-restricted-modules-2.6.23" for it to work. I have no idea on how to fix this. Any help?

---

### Post by Shyper on 2007-10-19
Bump?!?!

---

### Post by Shyper on 2007-10-19
Bump?

---

### Post by modulok on 2007-10-20
I had the same issue. I followed the wifi part after sound part and my wifi worked again.

---

### Post by white3454 on 2008-01-27
I have a D630, Intel 3945 wireless card and it kept dropping my connection and would not get a new IP address.  When I rebooted, you could see that Network Manager crashed/hung, uber annoying!

I actually tried to compile the driver from Intel and then compile a new Kernel... I've been using linux/unix for over 5 years and compiling the kernel was beyond me and is still freaking me out.

Luckly I reloaded the OS, and I found the following commands to stop the ipw driver and start using the iwl driver, which has been working like a charm

This will show you the drivers being used:

> lsmod | egrep 'Module|iwl|ipw'

Next, type this:

> sudo modprobe iwl3945

run this again:

> lsmod | egrep 'Module|iwl|ipw'

You should get this output:

> ubuntu@ubuntu-laptop:/etc$ lsmod | egrep 'Module|iwl|ipw'
Module                  Size  Used by
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211



it's important to see the iwl3945 and the iwlfifi_mac80211...  You will need to go to your restricted drivers and disable the ipw3945 driver and reboot.

Hope this helps...

---

