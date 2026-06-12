---
title: "Adding service name to a pppoe"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Snitz on 2008-03-28
I just want to understand why ubuntu's pppoe connections don't support "service names"?
At home, I need to enter a service name to my pppoe connection in order to connect to the internet and the service name is: Mnets\RES

Is there a way editing the (dsl-provider) file found in /etc/ppp/peers/ and add the service name?
I tried editing it but it said I don't have full permissions over that file or folder.

Please help.

---

### Post by talsemgeest on 2008-03-28
Well if you need to edit the file, type ```
gksudo gedit /etc/ppp/peers/(Filename here)
```

---

### Post by Snitz on 2008-03-28
That worked, here is the original file content.

> 
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
user "mak70"


I added 

> servicename "Mnets\RES"

After: user "mak70"

Would that work?

---

### Post by talsemgeest on 2008-03-28
Sorry, I know just about nothing about networking...

---

