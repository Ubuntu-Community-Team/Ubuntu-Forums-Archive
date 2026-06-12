---
title: "Which Ubuntu-Version for a home server (web, file), running on old hardware?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by plutox on 2008-01-20
Hello everybody,

I'm looking for a tiny linux/ubuntu based home server.
On the server should run lighttpd (because I'm familiar with that) with webdav and ssl, php, mysql, samba and a tiny, self-written app, that logs commands, received through a serial port, to a mysql-database.

The server should not have any gui. I'd like to use shell (via ssh) and webinterfaces to configure the server. I don't need any additional or "professional" server-features like quotas.

The server should run on moderate hardware, that is an epia-board (via c3 600 mhz cpu) with 256 MB RAM.

Which Ubuntu-Version suits best for my requirements? Ubuntu-Lite, the Desktop-Version, the Server-Version or is maybe the JeOS-Version good enough?

Is the alternative installer or the mini installer the right way?

Thanks for any help and tipps.

regards

plutox

---

### Post by bwhite82 on 2008-01-20
I would simply install 'ubuntu-minimal' to give you a working CLI-only setup and then install your apps from there.

Edit: The alternate installer will accomplish this for you.

---

### Post by PilotJLR on 2008-01-20
I would do the Server version... it does not come with X11, which is what you said you wanted.

Note that if you choose a "LAMP Install" with Server, it will install most of what you want (except apache2 instead of lighttpd).

---

