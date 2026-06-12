---
title: "Restarting X causes wireless connection to no longer work"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Mark20 on 2008-04-01
Hi all,

I sometimes need to switch between Fluxbox, and KDE sessions.  To do this, I simply restart X Windows (Using Control+Alt+Backspace).  But every time I do this, then try to reconnect to my wireless network, the wireless network connection never works.  Ever.  

Note:  I connect to my wireless network using the command line (because I still can't get KNetworkManager, or wicd to work).   But regardless, it works normally no problem.  EXCEPT, after I restart X.  If I restart my machine it works, but this is very time consuming...

Anyone know what's wrong?

---

### Post by forrestcupp on 2008-04-01
Go to System->Preferences->Sessions.  In the 'Startup Programs' tab make sure that Network Manager is in the list and enabled.  If not, then add a new one and name it Network Manager, and add this command
```
nm-applet --sm-disable
```

---

### Post by Mark20 on 2008-04-03
Ummmm...ok.  But I don't want KNetworkManager, I want to connect to the internet through the console, since I need to customize some of my wireless settings.

All I want to do is be able to restart a session, and be able to use my internet (aka be able to switch between KDE, and Fluxbox without restarting.

I've also looked into this a bit further, and noticed that even if I kill all dhclient process', my wireless card still has it's ip address (192.168.1.x).  Even after doing a ```
sudo ifconfig eth1 down
```  Is there a specific process that I need to kill that could be causing the problem??

---

