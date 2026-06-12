---
title: "azureus help"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by nick5449 on 2006-04-22
I cant seem to get Azureus to download anything.  The majority of the time I have no NAT errors and it seems like everything should be working okay.  The torrent will have a lot of seeds but I just cant connect to any of them.  If I do finally end up connecting to someone, the connection will be dropped pretty quick.  Im running Ubuntu Dapper and also have java installed and working fine. Thanks

---

### Post by htinn on 2006-04-23
Did you remember to set it as default?

```
sudo update-alternatives --config java
```

---

### Post by nick5449 on 2006-04-23
When I type that command i get: 
```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/jvm/java-gcj/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:
```

Which one should I be using?

---

### Post by user1397 on 2006-04-23
Do you have a firewall running? such as firestarter? if you do have firestarter, you might want to try opening firestarter in applications->system tools->firestarter,
and in firestarter, go to the policy tab, make sure you're in inbound policy, click on the blank space in the "allow service" part, and then click "add rule" and type in for port: 6881 and make it for evryone and click okay. that might do it.

---

### Post by nanotube on 2006-04-23
[QUOTE=nick5449]When I type that command i get: 
```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/jvm/java-gcj/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:
```

Which one should I be using?[/QUOTE]

you should be using number 3, the official sun java, because azureus seems to do better with it (as do a lot of other java apps). try it and see if it helps.

if not, the post about checking/disabling your firewalls is a sound idea - doesn't hurt to check if your firewall is at fault.

---

