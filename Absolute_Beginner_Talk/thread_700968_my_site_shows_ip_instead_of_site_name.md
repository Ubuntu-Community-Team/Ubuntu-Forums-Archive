---
title: "my site shows ip instead of site name"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Kuroda_Shun on 2008-02-18
I just got a site name, It points to my localhost. but it shows the ip address. how do I fis this?

---

### Post by Linux_Man on 2008-02-18
I believe it is DNS is what you need.

---

### Post by Kuroda_Shun on 2008-02-18
I got it with this
```
sudo apt-get install bind9
```

Then
```
sudo /etc/init.d/bind9 start
```
But it still doesn't show the name in the browser.
And thank you for your response.

---

### Post by lespaul_rentals on 2008-02-27
Get a dynamic hostname at [http://www.dyndns.com](http://www.dyndns.com).

---

