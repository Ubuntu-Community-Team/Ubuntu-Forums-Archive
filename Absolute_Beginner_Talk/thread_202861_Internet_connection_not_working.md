---
title: "Internet connection not working"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by poper on 2006-06-24
I've just installed Ubuntu for a week. After reinstalling (because of some boot-up troubles) the Internet connection doesn't work although the system identifies the ethernet card.

Using the recovery mode or the liveCD makes the connection work, but in a normal session it doesn't. This is the first it happens. The connection has always worked flawlessly.

3com OfficeConnect ADSL Wireless 11g router

Any idea please?

---

### Post by MaximB on 2006-06-24
try to confgiure your connection 
in the console/terminal enter :
"sudo pppoeconf"
hit return
and enter your password

---

### Post by poper on 2006-06-24
Thanks maxddark
pppoeconf show me this message:

> Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please &#9474; check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.   

and nothing else happens.

---

### Post by MaximB on 2006-06-24
make sure you've entered the correct username and password given you by your ISP

---

### Post by poper on 2006-06-24
Well, It's not needed to enter username/password to configure the connection in Windows or Ubuntu (I mean, username/password are stored in the router) for example, I don't enter them when using the Dapper LiveCD. That's weird because I've installed Dapper several times and always works (never asked for ISP username/password) until last time it went crazy (from a fresh installation)

Thanks for your answer.

---

### Post by poper on 2006-06-26
I've noted that if I disable the connection (which is not working) and then enable it again, the Internet connection begins to work. That's weird!

---

### Post by Apple 101 on 2006-06-27
That happens to me also, so it appears to be a bug of some sort.

---

