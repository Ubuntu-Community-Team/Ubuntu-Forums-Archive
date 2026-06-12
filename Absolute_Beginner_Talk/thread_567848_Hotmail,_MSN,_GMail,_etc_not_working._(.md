---
title: "Hotmail, MSN, GMail, etc not working. :("
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by foundation on 2007-10-05
Okay, so I got my net working (*Yay*!) but now I'm facing another problem, certain *connections* simply won't work, here's some examples:

Any type of secure site, like trying to log into Hotmail, GMail, my ISP (As in the site to check bandwidth usage, etc), Firefox extensions page, etc. Also, I can't log into any IM clients like Pidgin or the like so this isn't a problem restricted to a certain browser but rather with my *whole system*. :(

But what does work is.. well, everything it seems (HTTP, FTP, torrents, etc). **Any ideas?**

Edit: Here is the standard error I receive when trying to access any of the sites I listed just above:
```
Unable to connect

Firefox can't establish a connection to the server at www.google.com.   

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
```Yup, nothing useful. :(

Aside from this and 1 or 2 other small problems I'm loving 7.10, seriously, Canonical has done fairly well.. but if I can't get this working I might have to mostly stay in XP. D:

---

### Post by kerry_s on 2007-10-05
sounds like a dns issue.

[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by foundation on 2007-10-05
I can boot into XP on the same laptop and it's fine and no other computer on the network is having issues. :s

---

### Post by kerry_s on 2007-10-05
xp has dns built in, that's how they keep track of we're you go on line.

---

### Post by kvonb on 2007-10-05
How do you connect to the net?  Is it PPPoE by chance?

Sounds like a classic case of MTU too big.

If you are using pppoe, you need to edit /etc/ppp/peers/dsl-provider and change the MTU to a smaller number.  Mine is down to 1432, I was having the same issues and it was driving me insane!

---

### Post by foundation on 2007-10-05
kerry_, sorry, it simply isn't a DNS issue, if it was I wouldn't be able to access the site(s) at all but rather it cuts out when I try any type of *secure* connection.. and cause of this problem I can't even access the *Start* page on OpenDNS.com, hah. :x

kvonb, my router uses PPPoE (ADSL) and at the moment I'm using the wireless connection but I also have a network cable here (Usually in my X360) I can use if I need/want to.. the thing is though, if this was a problem related to the MTU or the like wouldn't it effect all the PCs on the network?

Either way, I'm desperate so I'll give our suggestion a go, thanks mate.

Edit: I tried *sudo gedit /etc/ppp/peers/dsl-provider* and it simply made a new file indicating there wasn't one already. Is there something wrong with the command or file address?

---

### Post by kerry_s on 2007-10-05
> **foundation said:**
> kerry_, sorry, it simply isn't a DNS issue, if it was I wouldn't be able to access the site(s) at all but rather it cuts out when I try any type of *secure* connection.. and cause of this problem I can't even access the *Start* page on OpenDNS.com, hah. :x

kvonb, my router uses PPPoE (ADSL) and at the moment I'm using the wireless connection but I also have a network cable here (Usually in my X360) I can use if I need/want to.. the thing is though, if this was a problem related to the MTU or the like wouldn't it effect all the PCs on the network?

Either way, I'm desperate so I'll give our suggestion a go, thanks mate.

Edit: I tried *sudo gedit /etc/ppp/peers/dsl-provider* and it simply made a new file indicating there wasn't one already. Is there something wrong with the command or file address?

ppp is dial up.

i'm sure your getting dhcp from the wireless router.

dropped sites are a common problem, when the isp's dns servers suck.

what do you have to lose, since you can't reach it i'll talk you through it.

press> alt+f2
type> gksudo gedit /etc/dhcp3/dhclient.conf
put> prepend domain-name-servers 208.67.222.222,208.67.220.220;
right under> #prepend domain-name-servers 127.0.0.1;
reboot

good luck.

---

