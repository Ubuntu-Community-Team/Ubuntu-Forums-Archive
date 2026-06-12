---
title: "Wireless Problems"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by k5ilf on 2007-04-26
I still am having problems getting my MA311 Netgear card to work with my system. I installed Feisty Fawn with Wubu and it appears to be working OK. The wiki indicates that the card should be supported by FF. Since I am dual booting, I have no direct access to the Internet from Ubuntu as my only connection is wireless. I really need a step by step process for attempting to connect. I have NO linux knowledge at all. Where can I find some assistance? The help files indicate selections which are not available to me.

Thanks for the assistance.

bill in las cruces

---

### Post by Kobalt on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You need to blacklist a number of things to have this card work out of the box. Open up a Terminal (Apps > Accesories > Terminal) and run this command : 
```
gksu gedit /etc/modprobe.d/blacklist
```
This will open up a text file, go straight to its end and add the following lines : 
> prism2
prism2_pci
hostap
hostap_pci
Reboot, and you're done. You can now configure your wifi connection from the top right network applet of yours (right click > configure) or System > Admin. > Networking.

---

### Post by k5ilf on 2007-04-26
Thank you Kobalt for the help.
I made the addition to the blacklist and rebooted and now the only option is to manually configure.
Now I still am having problems, I think!
Under wireless connection, I put the network name of ******** (my last name)
I don't know what to put under domain name, I have the scan option checked
under DNS 192.168.1.1
under hosts    local lhost 127.0.0.1
ubuntu   192.168.1.42

Any assistance would be appreciated, again :)

bill in las cruces

---

### Post by Quickened on 2007-04-26
> **Kobalt said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You need to blacklist a number of things to have this card work out of the box. Open up a Terminal (Apps > Accesories > Terminal) and run this command : 
```
gksu gedit /etc/modprobe.d/blacklist
```
This will open up a text file, go straight to its end and add the following lines : 

Reboot, and you're done. You can now configure your wifi connection from the top right network applet of yours (right click > configure) or System > Admin. > Networking.


I dont want to assume anything but i was wondering if i have to do the same thing to get my Netgear MA111 to work.

Any help or advice would be appreciated!

---

### Post by sailor2001 on 2007-04-26
system/networking  list as dhcp and allow in to automaticly configure.....install a wifi manager such as kwifi or wifi radar  (synaptics)

---

### Post by k5ilf on 2007-04-26
Thanks Sailor, I tried to use the auto config, but nothing happened. I try and install a different wifi manager and I get an intercept indicating that it would interfere with the included wifi manager. I also have no access to the Internet using Ubuntu.

bill in las cruces:confused:

---

