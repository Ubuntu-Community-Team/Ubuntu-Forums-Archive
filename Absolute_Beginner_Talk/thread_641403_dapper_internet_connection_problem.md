---
title: "dapper internet connection problem"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by gregoryham on 2007-12-15
i run dapper drake on a dell inspiron 8000 laptop. i had no problems connecting to the internet (dsl) from my home until a few days ago, when i tried to connect at my university and failed. at school, i poked around in system > preferences > network proxy, but since i didn't know what i was doing i changed nothing.

but now, my internet at home won't connect to normal web addresses, but i was able to connect to google through [http://72.14.253.147/](http://72.14.253.147/) with no problem. 

what happened? how can i fix it?

thanks!

---

### Post by toddward on 2007-12-15
It sounds like that might be a DNS server problem.  You might be able to just restart your networking and it should find the right DNS server.

Through the terminal you could also try restarting the network by issuing:
```
sudo /etc/init.d/networking restart
```

---

### Post by gregoryham on 2007-12-15
thank you!

---

### Post by toddward on 2007-12-16
gregoryham...please note that I had the incorrect command.  

You will get this error (most likely) if you enter that above command.
```

sudo: /etc/init.d/network: command not found

```

---

