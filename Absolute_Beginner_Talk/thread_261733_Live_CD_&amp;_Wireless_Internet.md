---
title: "Live CD &amp; Wireless Internet"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by cldnails on 2006-09-20
I've done search after search and to be honest I think I'm more confused than when I started. lol I have successfully installed ubuntu on a secondary PC, it has internet access through an ethernet card...so wired.

Now, I was happy with the install and everything this distro has to offer, so I went to install it on my main PC. However, I wanted to make sure I wouldn't have any issues, so I have been running the live CD...but I can't connect to the internet.

The device manager recognizes my wireless card and when I go to networking through the admin menu I'm given the option to activate it. It does activate, but it takes awhile, afterward I still cannot connect to the internet. The next time I go to the admin>networking it shows that it is not active.

Suggestions would be appreciated. I was basically wondering if I would have better luck if I wasn't running it off of the live CD, or if I would have these same problems once installed. Thanks in advance!

---

### Post by UltraMathMan on 2006-09-20
Are you attempting to connect to an encrypted network? If so what type of encrytption does it use?

---

### Post by cldnails on 2006-09-20
To keep things simple I released security on the network...no anything. Just straight connection...that's why I'm at a loss.

---

### Post by UltraMathMan on 2006-09-20
After activating the interface can you post the output of ```
iwconfig
``` and ```
ifconfig -a
```

---

