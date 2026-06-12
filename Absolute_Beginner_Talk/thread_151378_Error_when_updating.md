---
title: "Error when updating"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by The_Tankengine on 2006-03-27
I just ran apt-get update and I get this error message

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Any help for a n00b?

---

### Post by underwater on 2006-03-27
You don't have permission use sudo for root powers

sudo apt-get update

is the command you want to use

---

### Post by The_Tankengine on 2006-03-27
I swear I used sudo the first time, but I tried it again anyway and it worked.
Thanks for the magic touch!

---

### Post by cacahootie on 2006-03-27
Also keep in mind you can only use Apt once at a time, including Synaptic and Update Manager.  That problem will give you a similar error message.

---

