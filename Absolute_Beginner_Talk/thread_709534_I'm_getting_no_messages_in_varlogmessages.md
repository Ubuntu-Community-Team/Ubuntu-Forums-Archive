---
title: "I'm getting no messages in /var/log/messages"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by philinux on 2008-02-27
Well very few anyway. klogd and sysklogd are running too.

---

### Post by philinux on 2008-02-27
come on guys, you know there's a solution

---

### Post by Mr. C. on 2008-02-27
Use the logger command to test that syslog is logging:

```
logger This is a test
tail /var/log/messages

```
MrC

---

### Post by philinux on 2008-02-28
The logger command put that into messages. I think it must be klogd thats not doing it's stuff. I used to get loads of stuff in messages.

---

### Post by Mr. C. on 2008-02-28
What routine, periodic, or expected messages are you missing?  There's not much to go on other that "it sure is quite here - what's the problem?" !

MrC

---

