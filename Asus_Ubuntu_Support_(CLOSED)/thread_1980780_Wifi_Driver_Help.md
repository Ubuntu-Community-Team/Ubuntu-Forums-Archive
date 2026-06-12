---
title: "Wifi Driver Help"
date: 2012-05-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Spiffed0 on 2012-05-15
Hey guys, I am brand new to Ubuntu and Linux all together. I recently set up a dual boot with Ubuntu on my **ASUS U56E Notebook**. The problem is, whenever I boot with Ubuntu I can not connect to wireless networks. I have gone through countless forum posts and tutorials on how to get my wifi working. I was working through this ([https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)), But the drivers .inf files were not working for me. Any help would be greatly appreciated. 

Thanks.

Spiffed

---

### Post by WBMachinery on 2012-06-11
I have the same computer that had that problem, this should work for you also:

Type this command:
```
gksu gedit /etc/modprobe.d/iwl.conf

```

The editor should open, copy this to the file:
```
options iwlwifi bt_coex_active=0

```
Save , quit and reboot.

And that should be all 

To ensure fast internet type these commands.
```

sudo rmmod -f iwlwifi

gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf

options iwlwifi 11n_disable=1

```

---

### Post by texasmade1 on 2013-01-30
> **WBMachinery said:**
> I have the same computer that had that problem, this should work for you also:
 
Type this command:
```
gksu gedit /etc/modprobe.d/iwl.conf

```
 
The editor should open, copy this to the file:
```
options iwlwifi bt_coex_active=0

```
Save , quit and reboot.
 
And that should be all 
 
To ensure fast internet type these commands.
```

sudo rmmod -f iwlwifi
 
gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf
 
options iwlwifi 11n_disable=1

```
 
WBMachinery; I am having the same issue as the OP on my Asus U56E, with the only difference being that i'm running 12.04 only on the machine (no windows partition).  Will I need to modify your instructions any?  
 
When I plug an ethernet cord in, the internet works fine, but when I unplug the cord and try to connect to my wifi, it sees my SSID and then prompts me for the password.  After entering the correct password (I double checked that the caps lock key wasn't on, etc) it "tries" to connect and after 2-3 minutes it asks me for the password again.  This continues over and over.  Any help is much appreciated!

---

### Post by himicton on 2013-01-30
hi there new to Ubuntu
Dell Inspiron 1300, Broadcom wireless adapter
Problem: When i did a clean install of Ubuntu i cannot connect via wireless
Help very much appreciated

---

### Post by texasmade1 on 2013-01-30
> **himicton said:**
> hi there new to Ubuntu
Dell Inspiron 1300, Broadcom wireless adapter
Problem: When i did a clean install of Ubuntu i cannot connect via wireless
Help very much appreciated
 
i'm new to Ubuntu as well.  Looks like we are in the same boat with the wireless connectivity issue; just with different laptops.  What version of Ubuntu are you running?  I'm running 12.04.  I'll post up if I figure out a solution

---

### Post by texasmade1 on 2013-02-01
bump

---

