---
title: "hosts file syntax"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by nublaii on 2007-06-19
I have my machine behind a router, and the router forwards all the incoming traffic to my server.

So in fact, my machine answers to 127.0.0.1, 192.168.1.100 and 123.123.123.123

My machine is named 'bling', my internal network is 'lan' and it responds to the outside world as 'example.com'

What should be the correct hosts file for this?

Something like this?

```
127.0.0.1 localhost.localdomain localhost
192.168.1.100 bling.lan bling
123.123.123.123 example.com
```

---

### Post by EndPerform on 2007-06-19
The hosts file is used for resolving addresses on the local machine.  I wouldn't worry about putting every single address of your machine in your host file.  For example, here's mine:

```

127.0.0.1 localhost localhost.localdomain fry
192.168.1.50 scooby

```

Where fry is my box, and scooby is my other machine.  I would say if you had:

```

127.0.0.1 localhost.localdomain localhost bling

```

Your box should be fine.  I've forwarded traffic to my box from my router without an issue.  Hope this helps.

---

