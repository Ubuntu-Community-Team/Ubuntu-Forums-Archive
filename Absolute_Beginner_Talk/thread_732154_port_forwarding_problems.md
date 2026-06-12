---
title: "port forwarding problems"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by wsetchell on 2008-03-22
So right now I'm trying to forward requests from the internet to apache.  What I did wrong is I made it so, whenever anyone tries to access the ip of my router, they get forwarded to my website.  To make it so users get forwarded to the correct site, I need go to [http://myip](http://myip)  but by going there, I get directed to my website.  How can I change my router configuration when I keep getting re-directed to this site instead of where I need to be?

Thanks
-Will

---

### Post by Oldsoldier2003 on 2008-03-23
> **wsetchell said:**
> So right now I'm trying to forward requests from the internet to apache.  What I did wrong is I made it so, whenever anyone tries to access the ip of my router, they get forwarded to my website.  To make it so users get forwarded to the correct site, I need go to [http://myip](http://myip)  but by going there, I get directed to my website.  How can I change my router configuration when I keep getting re-directed to this site instead of where I need to be?

Thanks
-Will

use the internal ip address of your router... its probably 192.168.0.1

---

### Post by wsetchell on 2008-03-25
"its probably 192.168.0.1"

That address doesn't work.  How can I find the correct one?

---

### Post by Oldsoldier2003 on 2008-03-25
```
netstat -r
``` your default gateway is your router

---

### Post by wsetchell on 2008-03-27
Alright I've got access to my router configuration.  How can I find the address that I need to forward to?

Thanks
-Will

---

