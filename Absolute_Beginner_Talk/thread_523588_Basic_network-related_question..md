---
title: "Basic network-related question."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2007-08-12
I've got apache running, but how the hell do people know which computer to connect to? Because I give them my external IP, which is used across the internet, but I don't give them the specific internal IP of my webserver. How can I get people to connect to a specific computer (or webserver) on my network? Is this to do with settings in my router?

**Example**

* External IP for my network= 1.2.3.4
* Webserver IP= 10.1.1.3
* Other computers IP= 10.1.1.4

Client: "hmmmm... so i connect to 1.2.3.4 to find the site, hey, there's two computers on this network... wtf!??!!? Which one is the webserver?"

---

### Post by Warren Watts on 2007-08-12
You need to configure your router to forward port 80 (the HTTP port) to the machine running the server.  Any incoming HTTP requests it receives will then be forwarded on to your Apache server.

---

### Post by some_random_noob on 2007-08-12
> **Warren Watts said:**
> You need to configure your router to forward port 80 (the HTTP port) to the machine running the server.  Any incoming HTTP requests it receives will then be forwarded on to your Apache server.
Yep, its under "filters". I feel st00pid now... oh well, asking narrows it down I guess :)

---

### Post by Warren Watts on 2007-08-12
Hey, that's what this forum is here for.

Glad I could be of assistance!

---

