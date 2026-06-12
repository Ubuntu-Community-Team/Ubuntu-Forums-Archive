---
title: "configuring dhcp network???"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-04
Im trying to install right now, and like the fourth menu i gives the option to configure dhcp network manually.  I have a linksys broadcom card which i have read is a pain to install, so do i just not bother trying to configure, (its asking me to assign an ip address I think) and deal with wireless later??  Please advise, thanks!

---

### Post by vejan on 2006-04-04
just let dhcp assign the ipaddress automatically

---

### Post by x5452 on 2006-04-04
it doesnt, after the configuring the network with dhcp box runs, it says 
"network autoconfiguration failed"  then gives me the option to retry, configure network automatically, or not to configure at this time...

---

### Post by vejan on 2006-04-04
is the network cable plugged into the computer? in the network port , not the modem port???:)

---

### Post by RRS on 2006-04-04
You may have to install the driver for your card before the dhcp server can asign an address so select "not at this time" and continue the installation.

After you have Ubuntu up and running search the forums for help with installing and activating your card and once the connection is made the configuration should proceed automatically on the next boot.

---

### Post by mumushi on 2006-04-04
install the driver first then automatic configuration will work fine.

---

### Post by jamesr on 2006-04-04
After re-reading your posts, are these errors are occuring during the install process? if the answer is yes follow RRS's advice and  select "not at this time" and continue the installation.

Then once installed,  install the driver. 

There will a few consequences of this approach. The repository file (sources.list) will need to be editted to remove the CD as the first choice. You also may need to manually edit the network file (/etc/network/interfaces) and /etc/resolv.conf file.

If the answer is no then follow mumushi's advice.

---

