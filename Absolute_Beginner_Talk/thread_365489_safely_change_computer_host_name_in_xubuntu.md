---
title: "safely change computer host name in xubuntu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by ktusyn on 2007-02-19
ok i really need help call me a total noobie or what ever i run xubuntu. i have it set up to use mysql and apache and samba and a few others. i need a safe way to change my computer name.  right now my computer name is my dhcp clients ip and i need it changed so that it is not so dangerous to have. any help is welcome i know about the hosts and hostname file in the etc/ but not sure how to use it and not sure if that is the safest way to do it.

---

### Post by Bachstelze on 2007-02-19
First, get a root shell with *sudo -i*. Then run *hostname new_hostname* and edit /etc/hostname and /etc/hosts accordingly.

---

### Post by ktusyn on 2007-02-19
thanks will try to see if it is what i needed

---

### Post by kerry_s on 2007-02-19
menu> system> networking> general tab

---

### Post by ktusyn on 2007-02-19
i don't have that function to do that i don't know why mabye it was installed wrong or something but that does not work

---

### Post by kerry_s on 2007-02-19
What, maybe it's not in your menu, try pressing alt+F2 and put ->
gksu network-admin
 
or

menu> accessories> appfinder

and see if it's listed there. If not try reinstalling "xubuntu-system-tools" using synaptic.

Ohh, wait i just noticed your on dapper, i'm on edgy so it might have been added in edgy only. Sorry

---

