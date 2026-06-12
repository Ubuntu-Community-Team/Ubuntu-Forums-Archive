---
title: "Cannot Sleep"
date: 2012-02-02
forum: Apple Hardware Users
---

### Post by Slaco on 2012-02-02
Hey all,

So I've managed to get Xubuntu 11.10 running on my early 2011 15' MBP virtually flawlessly - pretty much everything is working as it should right now. There is one exception though (something that I'd be willing to overlook on my desktop, but not my laptop): sleep.

If I close the lid, the computer doesn't appear to make any attempt to go to sleep, the white light on the front stays lit for the entire time. The computer is still fully awake and functioning normally after opening the lid, just with the screensaver running.

If I manually put the computer to sleep through the menu, it just goes to the screensaver with the keyboard and trackpad usually becoming disabled (non-responsive) after that.

I'd appreciate any help, as I'd love to use Xubuntu more but simply can't if sleep isn't working.

Thanks in advance.

---

### Post by Slaco on 2012-02-10
No one?

---

### Post by CedarHawk on 2012-02-10
Just curious, are you running it as a standalone OS? Or as an application.

---

### Post by pauljwells on 2012-02-11
Sleep is a very tough thing to get working and almost always related to non-free drivers for hardware. Check the 'Restricted Drivers' program and revert to OSS versions to see if that helps.

---

### Post by Slaco on 2012-02-15
> **CedarHawk said:**
> Just curious, are you running it as a standalone OS? Or as an application.

I got a bit lazy, so it's a Wubi install.

> **pauljwells said:**
> Sleep is a very tough thing to get working and almost always related to non-free drivers for hardware. Check the 'Restricted Drivers' program and revert to OSS versions to see if that helps.

The only non-free driver I'm using is the proprietary ATI driver, as for some reason the open-source Radeon driver doesn't work properly for me. I'll give it another shot though.

---

### Post by bcbc on 2012-02-15
Check /var/log/syslog for any PM: exceptions.
```
grep 'PM:' /var/log/syslog
```
Or dmesg. After attempting to suspend:
```
tail /var/log/dmesg  # check end of log
less /var/log/dmesg  # browse all
```

---

### Post by winh8r on 2012-02-15
Old thread which is not aimed at 11.10 but it might give a few pointers as to where the solution might lie (maybe)

hope it is of some use


[http://ubuntuforums.org/showthread.php?t=471855&page=21]("http://ubuntuforums.org/showthread.php?t=471855&page=21")

---

### Post by Slaco on 2012-02-15
> **bcbc said:**
> Check /var/log/syslog for any PM: exceptions.
```
grep 'PM:' /var/log/syslog
```
Or dmesg. After attempting to suspend:
```
tail /var/log/dmesg  # check end of log
less /var/log/dmesg  # browse all
```

Alright I took a look at the log, and the culprit is indeed the proprietary fglrx driver. I uninstalled it and re-installed the open-source radeon driver, but that still is broken (why I installed fglrx in the first place :/).

Basically if I use the radeon driver, I get a totally black screen (the display doesn't even get power/signal) immediately after the boot screen. I'd appreciate any help getting this to work. BTW this MBP has a 6470M 'Seymore' videocard.

---

### Post by bcbc on 2012-02-16
What are the error messages you get?

---

### Post by Slaco on 2012-02-16
> **bcbc said:**
> What are the error messages you get?

You mean for the video error? I don't get anything, screen just goes dark after boot logo.

---

