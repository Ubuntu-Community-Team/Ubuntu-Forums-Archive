---
title: "Limiting Network Computers' Download"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by dacky on 2006-04-04
Our school is setting up a server (possibly Ubuntu) as gateway to 20-30 computers on our network (most of them will be Windows).  We want to filter internet content with this server.  We also want to limit how much students can download so it does not make it difficult for faculty and staff to use the same network (some of the connections will be in dormitories, and students could potentially rob all the bandwidth with big downloads).  How can we limit how much students can download?  Can Wondershaper limit the bandwidth of any computers attached to the server?  Is there another program we can install that can do this?  We have no money to get expensive hardware to do this.

---

### Post by JShadow on 2006-04-04
You should be able to do this using squid, a proxy server. There is a howto here. 

[http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html)

The building from source isn't necessary but the config file information should be applicable.

---

