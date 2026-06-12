---
title: "apt-get upgrade"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Mr.er on 2006-08-25
when typing 

```

sudo apt-get update && sudo apt-get upgrade

```


into the terminal, I get the following errors.

```

Get: 13 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Fetched 104B in 0s (224B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I have no idea how to go about fixing this. 

ANY help is very appreciated.

---

### Post by bulldog on 2006-08-25
This means that another package manager is running on your system.

Could be synaptic or update manager.
Be sure they are not in your panels and active.

---

