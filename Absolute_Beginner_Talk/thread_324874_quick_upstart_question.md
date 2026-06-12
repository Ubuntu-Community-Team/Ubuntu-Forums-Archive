---
title: "quick upstart question"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by viniosity on 2006-12-24
In Edgy, what's the proper way to stop/start a daemon service via the command line?  For instance, I used to use:

```

sudo /etc/init.d/samba stop

```

While that still works in Edgy I'm wondering if there is a preferred way to do it now given upstart is the way forward?

---

### Post by dbbolton on 2006-12-25
i think there might be something like 'sudo killall smbd'

---

### Post by viniosity on 2006-12-25
That will kill the process but it will not bring it down gracefully.  I don't think you would want to use a killall unless you had to.

---

