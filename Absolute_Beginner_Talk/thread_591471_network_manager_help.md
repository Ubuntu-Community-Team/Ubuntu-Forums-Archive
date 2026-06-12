---
title: "network manager help"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-10-25
Does anyone know how to shut this script down.  It is locking my computer at a constant rate.  I can not see anywhere with the GUI where I can shut it down.  Does anyone have a clue how to help me?  This command is locking my computer every hour.

***Oct 25 13:49:10 nyn-desktop NetworkManager: <info>  Updating allowed wireless network lists***. 

is there anyway NOT to allow it to update my wireless network?  Because I don't have one anyways.

the next line that comes up in my syslog is this.

[B][I]Oct 25 13:49:10 nyn-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
[/I][/B]
then followed by my computer locking up.

Noah

---

### Post by macogw on 2007-10-25
You could take NM out of your system > pref > sessions > startup
That'd keep nm-applet from starting up on each login, though I'm not sure it'd stop the daemon (also not sure that there is a daemon at all)

---

### Post by nynoah on 2007-10-25
But if I turn on network manager, I lose my internet connection.  I need to modify it so that it does not look for my nonexistand wifi card.

---

### Post by nynoah on 2007-10-25
Someone has to have a clue what is going on with this.  I have had to hard reboot my system 25 times today.

---

