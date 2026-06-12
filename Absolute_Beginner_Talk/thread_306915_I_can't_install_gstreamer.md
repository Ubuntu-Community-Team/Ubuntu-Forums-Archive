---
title: "I can't install gstreamer"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-25
I can't install the gstreamer using terminal. This is my command :
sudo apt-get install gstreamer0.10-plugins-ugly
I got errors after I type this command :
  E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
  E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by junglepeanut on 2006-11-25
make sure synaptic is closed, and that you are not trying to update in another terminal.

---

### Post by oliviacond on 2006-11-25
I got a new error :
E: Package gstreamer0.10-plugins-ugly has no installation candidate

---

### Post by CatKiller on 2006-11-25
Have you enabled the universe and multiverse repositories?

---

### Post by oliviacond on 2006-11-25
nope. I don't know how to.

---

### Post by CatKiller on 2006-11-25
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories)

:)

Each of those are good guides in their own right and are worth reading in their entirety. The "ugly" packages are in the Universe repository.

---

### Post by oliviacond on 2006-11-25
problem solved. :)

---

