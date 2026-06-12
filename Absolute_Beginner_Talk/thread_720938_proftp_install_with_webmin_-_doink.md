---
title: "proftp install with webmin - doink"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by thepiston on 2008-03-10
Stupid webmin cant' create my proftp.conf file or something, now I have a dead install.   Should I uninstall?  How can I get it to work?  I have someone else's file, but I'm not going to type all that by hand.  How can I cut and paste using webmin or something?

---

### Post by handydan918 on 2008-03-10
> **thepiston said:**
> Stupid webmin cant' create my proftp.conf file or something, now I have a dead install.   Should I uninstall?  How can I get it to work?  I have someone else's file, but I'm not going to type all that by hand.  How can I cut and paste using webmin or something?

What are we talking about, a headless server or something? Anyway, if you have ssh access you can do an scp like this 
scp filename.here target.ip_address.here:/Absolute/path/to/target/directory.here
hope this helps...

---

