---
title: "Apache2 Problems"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by leemobile on 2006-01-28
Hello Intorweb!

I was wondering if anyone can help me out:

I installed Ubuntu 5.10, and installed Apache2 using synaptic.

I threw in a test index.html into my http directory.

Firing up localhost on my machine with my web-browser allows me to see my test index.html.  BUT, trying to access it over the internet through another machine gets a time out and nothing is loaded.

Thanks,

Lee

---

### Post by hartnady on 2006-01-28
Configure your router to port forward port 80 to your computer.

---

### Post by leemobile on 2006-01-28
My internet connection isn't going through a router.

Any other ideas?

---

### Post by alamba on 2006-01-28
did u turn on the firewall on your machine?

Akshay

---

### Post by leemobile on 2006-01-28
*shrug*

I just installed Ubuntu with default settings.  The only thing I've installed so far is SSH and Apache2.

Does Ubuntu come with a firewall by default?

How do I check? 

Thanks!

---

### Post by alamba on 2006-01-28
Nope ubuntu does'nt have firewall with the default install. Maybe your ISP is filtering traffic to some ports.

Akshay

---

### Post by alamba on 2006-01-28
One good test would be to open the webpage by IP from a machine on the same LAN. If it open then it's your ISP.

Akshay

---

### Post by leemobile on 2006-01-28
Thanks a lot!

That's exactly what was the problem, my ISP is blocking my port 80, I completely forgot about that.

Cheers,

Lee

---

