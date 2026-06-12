---
title: "when am i running in root?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by cryo4.rm on 2007-07-26
i have to be honest ... i'm not ENTIRELY sure what running in root IS....

 for example..... have recently started using FIRESTARTER and it runs automatically on startup, but it wants to run in ROOT, ( at least, it asks me for my PASSPORT ..... which i assume is ROOT) so, from that point onwards am i then running root and leaving my system vulnerable?  But i suppose ... later actions in other areas require their own PASSWORD authorisation and so that means im not operating a insecure environment... (no?)

 i know its not a very clear question... will accept unclear answers..

 thanks. j.

---

### Post by aysiu on 2007-07-26
Root is the system user that has control over everything.

By default in Ubuntu you cannot log in directly as root, but many processes run as root.

It sets up a security layer--system processes, root; personal processes, user.

The first user automatically (and any other user manually added to the *admin* group) will have "sudo privileges," which means she can temporarily assume root (or administrative) privileges for a particular command after password authentication.

Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by mcduck on 2007-07-27
> **cryo4.rm said:**
> i have to be honest ... i'm not ENTIRELY sure what running in root IS....

 for example..... have recently started using FIRESTARTER and it runs automatically on startup, but it wants to run in ROOT, ( at least, it asks me for my PASSPORT ..... which i assume is ROOT) so, from that point onwards am i then running root and leaving my system vulnerable?  But i suppose ... later actions in other areas require their own PASSWORD authorisation and so that means im not operating a insecure environment... (no?)

 i know its not a very clear question... will accept unclear answers..

 thanks. j.

In that situation Firestarter is running as root, and you are running as your own user. Linux is a real multiuser operating system and can have many users on same machine at the same time.

Anyway, having root applications running all the time is less secure than not running them, but not even closely as bad as if you logged in to desktopas root yourself (as in that case _all_ apps would run as root instead of just Firestarter).

---

