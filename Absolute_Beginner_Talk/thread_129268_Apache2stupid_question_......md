---
title: "Apache2stupid question ....."
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by 008325 on 2006-02-13
i can connect to [http://localhost/index.html](http://localhost/index.html)

however , other people can not connect to my server 

how do i solve this problem ?

plx help >V<

---

### Post by uopjohnson on 2006-02-13
It is likely a firewall issue.  Do you have a router on your network?  Does it have port 80 forwarded to your server? 
The issue might also be on your ISPs end as some of them block port 80 by default.  If this is the case then you will want to try changing the port that apache is running on to see if you can get a connection there.

---

### Post by Liakoni on 2006-02-22
Can i ask how to change the port apache listens ?

---

