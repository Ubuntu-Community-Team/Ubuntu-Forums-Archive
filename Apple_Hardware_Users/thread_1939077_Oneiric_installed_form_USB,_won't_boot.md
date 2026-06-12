---
title: "Oneiric installed form USB, won't boot"
date: 2012-03-10
forum: Apple Hardware Users
---

### Post by rorschachwalter on 2012-03-10
I installed rEFIt, then made a USB stick with unetbootin. It boots into a live system just fine, and it installed just fine (apparently). The system boots into rEFIt, then I select Linux and it gives me a GRUB screen.

During boot, however, I get some errors. The boot experience is different each time.

Every boot results in strange graphical issues. I will either not see the Ubuntu loading splash at all, or I will see it in ugly text briefly before it get prettier, but smaller and in the upper left quadrant, and then it disappears entirely (leaving a purple background) to make way for some terminal output, including letting me know that system v failed.

Some boots skip the Ubuntu splash entirely and leave me with a black background with some terminal text output. The most recent boot says:
```
ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
ieee80211 phy0: wl_ops_bss_info_changed: arp filtering : enabled true, count 0 (implement)
ieee80211 phy0: wl_ops_bss_info_changed: arp filtering : enabled true, count 1 (implement)

mountall: Plymouth command failed
mountall: Disconnected from Plymouth
```Any ideas?

---

### Post by 2F4U on 2012-03-11
Did you follow the steps outlined in the Ubuntu/Mac documentation for synching rEFiT?

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu)

This forum section may also be helpful:

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by rorschachwalter on 2012-03-11
Those instructions don't even seem to be necessary for me -- rEFIt came up just fine, with Linux listed as an option, without my having to do anything. It can obviously find GRUB and go through the boot process for a bit. So, unless I'm missing something (I don't understand this whole rEFIt thing), I don't think partitions and rEFIt are the problem. Again, it boots GRUB and starts booting the OS, it just has issues during boot.

---

### Post by Splooshie123 on 2012-03-12
Nevertheless, you should see if rEFIt offers to sync partitions.

Graphical issues, hmm.... What model of Mac are you using?
Have you installed the proprietary nvidia graphics driver? If you have, try removing it. If you haven't, try installing it.

---

### Post by rorschachwalter on 2012-03-13
I'll check about syncing partitions when I get access to the Macbook again.

The Macbook is a 6,1 model. I haven't tried installing or removing nVidia drivers -- I can't get far enough into the system, even in safe mode, to manage packages :(

---

