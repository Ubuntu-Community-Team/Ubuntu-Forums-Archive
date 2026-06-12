---
title: "Proxy On Synaptic"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2007-01-16
Hi, 
I a using a proxy to use the nwt. And wen i try to write that proxy in synaptic it hangs, doesnt do anything any reason y this is so and how can i set the proxy, coz i really need some packages.

---

### Post by public_void on 2007-01-17
I used to be behind a proxy and had the same problem, I edited /etc/apt/apt.conf and put the following in, substituting my proxy settings in.

```

ACQUIRE {
http::proxy "http://user:password@proxy:portnum/"
}
```

IIRC then you set the network options to direct connection, I'm not sure why, but it worked for me.

[Here the thread I found the answer from.]("http://ubuntuforums.org/showthread.php?t=63496&highlight=apt.conf+http+proxy")

---

### Post by [S|G] on 2007-01-17
Ops, didn't see that there was an answer, sorry

---

