---
title: "sudo in rc.local"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-10-22
I got a fairly straightforward question for once.  XD

In my /etc/rc.local file, I have a few things running (opening ports for bittorrent is actually the only thing right now).  But I'm wondering, does rc.local execute with sudo privileges?  I'm asking because, for some reason, my /etc/hosts file is re-written each time I log in, and doesn't include my subdomains...  Here, let me illustrate.

When I log in, my /etc/hosts file has the following line at the top:

127.0.0.1 localhost

This is all good and well, except that I have a few test sites I'm trying to develop, so I sub-domained my localhost.  I edit it to read:

127.0.0.1 mysql.localhost fpji.localhost fpj.localhost auron.localhost family.localhost localhost

Getting tired of having to do this every time I booted up, I was wondering if I could just save the edited hosts file as /etc/hosts.bak, and then have rc.local execute "cp /etc/hosts.bak /etc/hosts" or if I needed to add a "sudo" to it, or what?

Thanks for the time.

---

### Post by kerry_s on 2007-10-22
rc.local runs as root.

localhost should be first and your sub-domained's after or you can just add another line.
example:
127.0.0.1 localhost
127.0.0.1 mysql.localhost fpji.localhost fpj.localhost auron.localhost family.localhost 


your also missing your name on the 127.0.0.1 line, it should be localhost and the name of your system which is on line 127.0.1.1.
mine:
127.0.0.1	localhost debian
127.0.1.1	debian

---

### Post by Sarteck on 2007-10-22
Oi, thanks!  ^_^

And yeah, my second line has my name, "127.0.1.1 Auron"

---

### Post by kerry_s on 2007-10-22
> **Sarteck said:**
> Oi, thanks!  ^_^

And yeah, my second line has my name, "127.0.1.1 Auron"

so your first line should be->

**127.0.0.1 localhost Auron**

---

