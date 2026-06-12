---
title: "Installing printer problems"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-12-11
I'm trying to use [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900") guide to install my canon LBP-1120 printer, but Im getting stuck at this line:

```
sudo /usr/sbin/lpadmin -p LBP1120 -m CNCUPSLBP1120CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
```

This is what I get when I try and put that in,
```

jussi@jussi-laptop:~$ sudo /usr/sbin/lpadmin -p LBP1120 -m CNCUPSLBP1120CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
lpadmin: Unable to connect to server: Connection refused
jussi@jussi-laptop:~$ 
```
 
can someone help?

---

### Post by Jussi01 on 2006-12-11
Never Mind - sorted - I needed to restart the computer :rolleyes:

---

