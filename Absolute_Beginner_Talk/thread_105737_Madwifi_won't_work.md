---
title: "Madwifi won't work"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by rikoshay on 2005-12-19
Hi, I'm trying to use madwifi to configure a Netgear WG511T card that didn't work straight out of the box. I added:

```
deb ftp://debian.marlow.dk/ sid madwifi
deb-src ftp://debian.marlow.dk/ sid madwifi
```

To my repositories list and then did:
```
sudo apt-get install madwifi-source madwifi-tools
```

After following the how-to in these forums I added ath_pci to my /etc/modules but nothing has appeared in the System->Administration->Networking other than the ethernet connection I'm already using. Following the newbie guid on madwifi.org this is what I get:

```
rik@lappy:~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta
Password:
sudo: wlanconfig: command not found
rik@lappy:~$

```

Any suggestions?  

Thanks!

---

