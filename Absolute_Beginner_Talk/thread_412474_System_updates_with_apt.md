---
title: "System updates with apt"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Sulli on 2007-04-18
G'day all

I am having an issue with using APT.

when ever i use the command sudo aptitude upgrade i get an awful lot of the following:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)

Also whenever i use add/remove programs or synaptic package manager i always get a message saying the file downloads as failed.

Also when i input the previous command i get the following message and have no idea what it means 

Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release

If Anybody has any ideas what is causing this, that would be great

If anybody needs any more info please ask as i dont quite know what other info to give.

thanks heaps 

Sulli

---

### Post by tchoklat on 2007-04-18
What version of Ubuntu are you using and are you using the repositories thta are installed automatically or have you changed the repositories (sources.lst)?

---

### Post by Sulli on 2007-04-18
I have ver 6.10 and i have not edited the sources.list

---

### Post by bapoumba on 2007-04-18
hello,
looks like a DNS problem. Please check out [this link]("http://ubuntuforums.org/showthread.php?p=2434983") (and actually the quoted links in it).

---

### Post by Sulli on 2007-04-18
Thanks heaps bapoumba changing the DNS settings did the trick

---

### Post by bapoumba on 2007-04-18
You're very welcome. Glad to see you got it to work.

---

