---
title: "Loaded VMPlayer now can't load VMServer"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by arochester on 2006-12-03
I previously loaded and used VMPlayer. I have now tried to follow the instructions in "HowTo: Windows (XP) on Ubuntu with VMWare Server" at [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

I get to the point of executing the installation script when I get the message:

A previous installation of VMware software has been detected.

Failure

Execution aborted.

How can I install VMWare Server?

---

### Post by Spin Doctor on 2006-12-03
I belive you cant have both vwware player and server installed on the same system. 

I tried Ubuntu using wmware player first before moving completely to Ubunt. I found, using the wmware player gives you a faster user experience of the virtual machine, but I needed to configure the virtual machine in WMware server, since the sound did not work for me. So I had to uninstall WMplayer, install WMserver, do my configuration changes, Unistall WMserver, and install WMPlayer.... =) What a hassle it was! =)

---

### Post by lamego on 2006-12-03
You can not have the bothes.
After uninstalling vmware you will also need to delete the vmware config with:
```
sudo rm -rf /etc/vmware
```

---

### Post by zami on 2007-03-12
> **lamego said:**
> You can not have the bothes.
After uninstalling vmware you will also need to delete the vmware config with:
```
sudo rm -rf /etc/vmware
```

I know this is old, but THANK YOU for sharing that!!  I've been trying to completely remove VMWare Player so I could install VMWare Server for the last hour - just couldn't figure out what little tidbit of the Player I was leaving behind.

Again, THANK YOU!!

-zami

---

