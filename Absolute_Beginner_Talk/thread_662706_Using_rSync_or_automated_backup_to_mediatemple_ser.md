---
title: "Using rSync or automated backup to mediatemple server?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2008-01-09
I have a server with Mediatemple web hosting and I have been thinking of using some of the massive hard drive for backups?

What is the best way to do this?

Also, if anyone knows of any other applications that I can use in conjunction with my server please do let me know as I would like to give them a go.... might aswel make the most of what I have already! :)

---

### Post by njparton on 2008-01-11
Is the server remote or local?

If local, share the hard drives on the server, mount them via NFS or CIFS in ubuntu and then you should be able to rsync to them no problem.

If the server is remote, you need to rsync via an ssh (or maybe vpn) tunnel for security.

---

### Post by beercz on 2008-01-11
Have a look at [http://rsnapshot.org/](http://rsnapshot.org/)

---

### Post by tigerplug on 2008-01-11
Just abou to head home from work.... will take a look at that when I get home in about 20 Minutes. ;) 

Thanks for the reply.

---

