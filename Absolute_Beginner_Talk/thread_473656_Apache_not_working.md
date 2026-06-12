---
title: "Apache not working"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Jimcanoa on 2007-06-14
Hello everyone,
apache2 used to work in my computer but I don't know what happened but I can't open [http://localhost](http://localhost) anymore... It gives me an error message saying "The connection has timed out".
Does anyone know what could have caused this?

Thanks

---

### Post by Cypher on 2007-06-14
Check that the Apache2/HTTP service is running by opening a termainl (Applications->Accessories->Terminal) and type
```

ps -eaf | grep apache
ps -eaf | grep http

```
One of those should yield about 4-6 instances of the appropriate name. If you see them, then we will need to dig further. However, if both those commands yield nothing, then you have to start the Apache service with
```

sudo /etc/init.d/apache2 start

```

---

### Post by jasonlfunk on 2007-06-14
Make sure that if you have a firewall installed, it lets through port 80.

---

