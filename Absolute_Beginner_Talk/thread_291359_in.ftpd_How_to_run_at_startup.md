---
title: "in.ftpd: How to run at startup?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by gborges on 2006-11-02
Hey all,

I need to use in.ftpd in my installation.  Grabbed it and installed it via the Synaptics Pkg manager.

I can see it in /etc/inetd.conf.  Problem is, it won't run at startup.  I can run it directly by /usr/sbin/in.ftpd.

I've re-installed it but no luck.

How do I get in.ftpd to run at startup?

Thanks.

---

### Post by flixer on 2006-11-02
Add /usr/sbin/in.ftpd to system -> prefenrences -> sessions -> startup programs

---

