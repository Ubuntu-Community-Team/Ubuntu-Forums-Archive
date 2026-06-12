---
title: "Firewall"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-11-30
Can anyone recommend a great firewall that will take advantage of "IP Tables"?

---

### Post by dpar on 2007-11-30
Um, I believe iptables IS your firewall.

---

### Post by Flyingjester on 2007-11-30
dunno if it makes use of ip tables, but i've been using firestarter and i find it adequate.

---

### Post by fmbugdadi on 2007-11-30
oh, ok, how do you run ip tables ?

---

### Post by Flyingjester on 2007-11-30
iptables is automatically enabled at install.

---

### Post by FuturePilot on 2007-11-30
> **Flyingjester said:**
> dunno if it makes use of ip tables, but i've been using firestarter and i find it adequate.
Firestarter is the graphical front end configuration tool to ip tables.

> **fmbugdadi said:**
> oh, ok, how do you run ip tables ?
It's always running. You can use Firestarter to configure it.

---

### Post by wormser on 2007-11-30
> **FuturePilot said:**
> Firestarter is the graphical front end configuration tool to ip tables.  It's always running. You can use Firestarter to configure it.

FururePilot is right.  Most people use Firestarter to manage IPtables.

```
sudo apt-get install firestarter
```

---

### Post by ruibernardo on 2007-11-30
After you install Firestarter as FuturePilot and wormser said, set it up as described here:

[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

---

### Post by fmbugdadi on 2007-11-30
thanks, that command worked....

---

### Post by mattchess on 2007-11-30
A bit confused - so does firestarter always need to be running to be firewalled, or is it just a front end to manage the built in firewall?

---

### Post by Dr Small on 2007-11-30
> **mattchess said:**
> A bit confused - so does firestarter always need to be running to be firewalled, or is it just a front end to manage the built in firewall?
It is just the frontend that manages iptables.

---

### Post by mattchess on 2007-11-30
Thank you...and at the risk of sounding completely dense...I assume that means that after I shut down firestarter, no inbound traffic that I have not allowed will be permitted.  Does iptables send any messages to let you know that something requested access that is not on the allowed list, or do I need to periodically check firestarter to see that in the events log?

Thanks again for your quick response.  Really great community here :-)

---

### Post by frank002 on 2007-11-30
After you shut down Firestarter, IPTABLES, which is the actual firewa,ll still keeps running. All Firestarter does is let you configure IPTABLES to your liking.The only time you bring up Firestarter is if you want to change a setting in the firewall.

---

### Post by mattchess on 2007-11-30
Perfect.  Thank you!

---

### Post by frank002 on 2007-11-30
You're welcome.

---

