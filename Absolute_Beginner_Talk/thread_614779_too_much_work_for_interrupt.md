---
title: "too much work for interrupt"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by leader303 on 2007-11-16
hi everyone!
there's a message right before the logon screen appears: blabla, too much work for interrupt 3. could that cause any problems? and even if not, how can i fix it?:)

---

### Post by ddrichardson on 2007-11-17
What kind of network card do you have?

---

### Post by leader303 on 2007-11-17
ralink rt2500 series wlan adapter. and it works.

---

### Post by ddrichardson on 2007-11-17
Is there anything listed in dmesg?

---

### Post by leader303 on 2007-11-17
```
[   23.916000] ra0: Initial auth_alg=0
[   23.916000] ra0: authenticate with AP 00:01:e3:41:ff:bd
[   23.916000] ra0: RX authentication from 00:01:e3:41:ff:bd (alg=0 transaction=2 status=0)
[   23.916000] ra0: authenticated
[   23.916000] ra0: associate with AP 00:01:e3:41:ff:bd
[   23.916000] ra0: authentication frame received from 00:01:e3:41:ff:bd, but not in authenticate state - ignored
[   23.920000] ra0: RX AssocResp from 00:01:e3:41:ff:bd (capab=0x411 status=0 aid=4)
[   23.920000] ra0: associated
[   23.920000] ra0: association frame received from 00:01:e3:41:ff:bd, but not in associate state - ignored

```
an later
```
[   32.484000] ra0: duplicate address detected!

```

that should be everything about the network adapter.

---

### Post by ddrichardson on 2007-11-17
duplicate address means that the address is already assigned - is this on a network or stand alone?

---

### Post by leader303 on 2007-11-19
my machine is always connected to internet and my flatmates' machines via wlan.
is there a clever command to display and change adresses?

---

### Post by ddrichardson on 2007-11-19
I shouldn't be too concerned unless you are getting problems with the connection. It could be that there is something slightly incorrect being received.

---

