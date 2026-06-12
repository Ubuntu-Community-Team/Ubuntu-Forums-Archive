---
title: "Web page can't be found"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by bruciee on 2006-08-24
Hi have just installed version 5.10 install went ok but am having trouble getting web pages to come up. If I put in [WWW.google.com](WWW.google.com) it comes up with an ALERT: [www.google.com](www.google.com) could not be found. Please check name and try again. I've checked my IP address and the ethernet connection is active.

---

### Post by ciscosurfer on 2006-08-24
Try disabling the connection then reenabling```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by mssever on 2006-08-24
What happens if you do```
ping google.com
```

---

### Post by ciscosurfer on 2006-08-24
Pinging google will have the same effect: a timeout

---

