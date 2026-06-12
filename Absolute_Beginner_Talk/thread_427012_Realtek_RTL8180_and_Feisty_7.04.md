---
title: "Realtek RTL8180 and Feisty 7.04"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by TEDNUGNT on 2007-04-29
Could someone please help me out and tell me how get my wireless card RTL8180 working? I have 7.04 running on a Dell Inspiron 8100. The card is a TrendNet TEW226.

I have read about using ndiswrapper or simply 'unblacklisting' the driver on the forums.

Please help. Thanks.

---

### Post by Kobalt on 2007-04-29
The disabled modules can be found in the /etc/modprobe.d/blacklist file. 
If you want to unblacklist them you need to edit the file : ```
gksu gedit /etc/modprobe.d/blacklist
```
At the end of the file you should find this section concerning your hardware : > # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
Make it look like this in order to authorize the modules to load at boot time : > # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
# blacklist r818x
# blacklist r8187
Reboot and you should be set. **Beware** : as you can read it may cause kernel bugs.

---

### Post by Metacarpal on 2007-04-29
Right now, there are some known issues with the Realtek cards and Feisty.  From what I understand, the easiest workaround (at least, until this is fixed by the devs) is to uninstall network-manager and install wifi-radar, in addition to the step Kobalt posted.

---

### Post by alan34 on 2007-04-29
In network manager you have to add an extra letter at the end of your network ESSID


eg      mywireless become mywirelessX

Had the same trouble myself good luck

---

### Post by TEDNUGNT on 2007-04-30
thanks so much everyone.

i will try what you have suggested and then undo the changes when i buy a new card.

can you direct me to the link of 'recommended' wireless cards for ubuntu or for that matter is there a website/link that discusses what hardware is recommended/compatible in general.

---

### Post by the_dark_light on 2007-05-06
Removing the driver (well rather commenting it out) in the blacklist file seems to "sort of" work.

The card is picked up by network manager and it detects my wireless network.  After entering the appropriate credentials to access the network (128bit WEP passphrase) it attempts to connect and then network manager reports no connection.

I'm thinking I could try ndiswrapper, but I've had mixed luck with that in the past

---

