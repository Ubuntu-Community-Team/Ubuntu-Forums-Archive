---
title: "ath0 available only as root"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by bavs on 2005-12-23
hi guys
so how do i give every user access?

i tried something and now i get
:~/Desktop$ modprobe ath_pci
WARNING: Could not open '/lib/modules/2.6.12-10-686/volatile/ath_hal.ko': No suc h file or directory
WARNING: Could not open '/lib/modules/2.6.12-10-686/madwifi/wlan.ko': No such fi le or directory
WARNING: Could not open '/lib/modules/2.6.12-10-686/madwifi/ath_rate_sample.ko':  No such file or directory
FATAL: Could not open '/lib/modules/2.6.12-10-686/madwifi/ath_pci.ko': No such f ile or directory

 anywhere i can get some help on removing and reinstalling the drivers?

---

### Post by Lambert on 2005-12-25
modprobe is the command that needs root privledges but you shouldn't have to insert it into the kernel. When the device is added to the system the kernel does this automatically. run this command.

lsmod | grep ath

if you just get the next prompt then it's not loaded. 

Do you have sudoers privledges? just add sudo infront of the command to modprobe

sudo modprobe ath_pci

make sure you have linux-restricted-modules for your kernel installed. this is where the madwifi module/driver is located.

```
sudo apt-get install linux-restricted-modules-`uname -r`
```

It's on the install cd

After installed plug your card in, everything should load ok. go to system>administration>networking. If your card is listed then driver is loaded and working.  set properties and activate.

Depending on your network settings there may be some other configuration edits that need to be made.

---

