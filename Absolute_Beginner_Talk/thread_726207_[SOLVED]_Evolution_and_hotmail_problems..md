---
title: "[SOLVED] Evolution and hotmail problems."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-16
I have made used all the settings from below link:

[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

but I get below error message:

Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Hotmail said you must pay money to have WebDAV access

Please enter the POP password for [email]h0glund@hotmail.com[/email] on host 127.0.0.1

Is there a way around this problem?

---

### Post by olskar on 2008-03-16
Try open the file /etc/hosts.allow

Add the line:
hotwayd: 127.0.0.1


and save it and exit.

---

### Post by lover_of_sc on 2008-03-16
I am afraid the same message appeared again mate?

---

### Post by Oldsoldier2003 on 2008-03-16
> **lover_of_sc said:**
> I am afraid the same message appeared again mate?

hotmail won't let newer accounts pop without paying a fee. it seems that some older accounts could still pop without paying the premium fee, but its subject to change at any time.

---

### Post by lover_of_sc on 2008-03-16
Ah alright, thats really poor of MS to charge for that. 

Not very surprising though, where can I find out if/when it's solved mate?

---

