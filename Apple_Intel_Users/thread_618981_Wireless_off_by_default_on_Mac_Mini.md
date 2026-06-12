---
title: "Wireless off by default on Mac Mini"
date: 2007-11-21
forum: Apple Intel Users
---

### Post by btrichardson on 2007-11-21
Hello all,

I'm using a Mac Mini to run Ubuntu 7.10 at work.  My office is inside a secure area that restricts the use of wireless devices.  Each time I reboot my Mac Mini, the built-in wireless is enabled by default.  Currently, I'm manually disabling it by right-clicking on the network icon up by the power button and un-checking the "Enable Wireless" option.

Is there a way I can configure Ubuntu such that the wireless is disabled automatically on reboot?  I've commented out "auto ath0" and "auto wlan0" in the /etc/network/interfaces file, but the "Enable Wireless" option is still checked each time I reboot, and ifconfig shows the wireless interfaces ath0 and wifi0 as up.  If it comes down to it, I'm willing to blacklist the kernel module for the wireless device if someone is willing to step me through that process.

As a side note, what's the difference between ath0, wlan0, and wifi0?

Thanks in advance!!!

---

### Post by cyberdork33 on 2007-11-21
The hardware is activated if the module is loaded...

Blacklisting 101:
```
gksu gedit /etc/modprobe.d/blacklist
```

at the end of the file just add 'blacklist *module_name*' for each module you want to block

For example, I hate the bcm43xx module for broadcom cards, and it will try to load automatically if it can... so I add:
```
blacklist bcm43xx
```

the module you want to black is probably ath_pci

Those names are just different ways that drivers make their appearance in linux.

---

### Post by btrichardson on 2007-11-21
Thanks for the blacklist 101 course, that's just what I needed!  Is there a way to determine for sure what module needs to be blacklisted?

Thanks!

---

### Post by cyberdork33 on 2007-11-21
> **btrichardson said:**
> Thanks for the blacklist 101 course, that's just what I needed!  Is there a way to determine for sure what module needs to be blacklisted?

Thanks!

I am pretty sure you have an atheros card. the command 'lsmod' will list all the currently loaded modules, (and grep will filter that).

```
lsmod | grep ath
```


I don't have any atheros cards, so I am not sure of all the modules that are loaded for yours. pretty much anything that has  'ath_*' or '*_ath' will be related to the atheros drivers though.

---

### Post by btrichardson on 2007-11-21
wow, you're fast! :)

Here's what I get when I run lsmod | grep ath
```

aaaaa@bbbbb:~$ lsmod | grep ath
ath_rate_sample        14208  1 
ath_pci                      98336  0 
wlan                        206660  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal                    192720  3 ath_rate_sample,ath_pci

```
I plan on blacklisting ath_rate_sample, ath_pci, and ath_hal.  This will do *something* to wlan since it looks like wlan depends on a few of these.  It also looks like 4 other things depend on wlan.  I guess my question is, what happens to modules when they depend on modules that are blacklisted?

Also, after adding modules to the blacklist, do I have to restart the computer, or can I run another command to activate the blacklisting?

Thanks!

---

### Post by cyberdork33 on 2007-11-21
> **btrichardson said:**
> wow, you're fast! :)

Here's what I get when I run lsmod | grep ath
```

aaaaa@bbbbb:~$ lsmod | grep ath
ath_rate_sample        14208  1 
ath_pci                      98336  0 
wlan                        206660  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal                    192720  3 ath_rate_sample,ath_pci

```I plan on blacklisting ath_rate_sample, ath_pci, and ath_hal.  This will do *something* to wlan since it looks like wlan depends on a few of these.  It also looks like 4 other things depend on wlan.  I guess my question is, what happens to modules when they depend on modules that are blacklisted?

Also, after adding modules to the blacklist, do I have to restart the computer, or can I run another command to activate the blacklisting?

Thanks!

I believe all those modules depend on ath_pci (you can see next to that module that it depends on nothing...). I would try just ath_pci first. The others should not load since you blacklist the original module (they are all for wireless stuff anyway).

Also , you can unload modules immediately with rmmod or modprobe -r

```
sudo modprobe -r ath_pci
```-or-
```
sudo rmmod ath_pci
```it may fail if it is "in use"

---

### Post by btrichardson on 2007-11-21
Awesome.  Thanks for the help.  I'm not physically in front of my Mac Mini right now, and I'm scared to do any of this via the command line since I need to keep the machine up and running through the Holidays.  I'll try all this out first thing next week.

Thanks again!

---

### Post by cyberdork33 on 2007-11-21
> **btrichardson said:**
> Awesome.  Thanks for the help.  I'm not physically in front of my Mac Mini right now, and I'm scared to do any of this via the command line since I need to keep the machine up and running through the Holidays.  I'll try all this out first thing next week.

Thanks again!

Oh party pooper!

Ok, probably a good idea what with the recent malicious commands that have been posted in the forums recently.
[http://ubuntuforums.org/announcement.php?f=211](http://ubuntuforums.org/announcement.php?f=211)

---

### Post by btrichardson on 2007-11-27
Does anyone happen to know what module is used for the Bluetooth card in the Intel Mac Mini?

---

### Post by cyberdork33 on 2007-11-27
> **btrichardson said:**
> Does anyone happen to know what module is used for the Bluetooth card in the Intel Mac Mini?

If you are trying to unload it, execute this:
```
sudo /etc/init.d/bluetooth stop
```I am unsure of the actual name of the module right now... it might just be "bluetooth"

---

### Post by btrichardson on 2007-11-27
> **cyberdork33 said:**
> If you are trying to unload it, execute this:
```
sudo /etc/init.d/bluetooth stop
```I am unsure of the actual name of the module right now... it might just be "bluetooth"

I think I've done that already by going to System -> Administration -> Services and un-checking the "Bluetooth device management" service.  I would just rather be better safe than sorry when it comes to the area my office is in... :)

---

### Post by cyberdork33 on 2007-11-27
> **btrichardson said:**
> I think I've done that already by going to System -> Administration -> Services and un-checking the "Bluetooth device management" service.  I would just rather be better safe than sorry when it comes to the area my office is in... :)
That may only stop the bluetooth tray icon, and bluetooth could still be active.

---

### Post by btrichardson on 2007-11-27
> **cyberdork33 said:**
> That may only stop the bluetooth tray icon, and bluetooth could still be active.

After testing, I've confirmed that it is the same as /etc/init.d/bluetooth

---

### Post by cyberdork33 on 2007-11-27
> **btrichardson said:**
> After testing, I've confirmed that it is the same as /etc/init.d/bluetooth
good deal.

---

