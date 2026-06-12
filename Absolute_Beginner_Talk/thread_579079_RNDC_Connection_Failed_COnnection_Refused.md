---
title: "RNDC: Connection Failed: COnnection Refused"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-10-17
Hey guys. I am currently trying to restart my BIND server, but whenever I do, I get this error:
```

rncd: connection failed: 127.0.0.1#953: Connection Refused
```

Does anyone know how I can fix this? Thanks.

---

### Post by JacobSteelsmith on 2007-10-18
Try using this command:

service named restart

Then look at /var/log/messages.0 and see if you can see any errors.

But this problem seems to be a permissions problem. 

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=J3M&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=rndc:+connection+failed:&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=J3M&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=rndc:+connection+failed:&spell=1)

---

### Post by drndrw on 2007-10-18
Uh that command does not work for me... what should I do?

---

### Post by drndrw on 2007-10-20
Sorry for the double post, but I am still having this problem. Thanks!

---

### Post by Dr Small on 2007-10-20
Maybe:
```
sudo /etc/init.d/rncd restart
```
??

---

### Post by drndrw on 2007-10-20
It says there is no command like that.

---

