---
title: "Mount on startup"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Samy_Merchi on 2006-05-19
I have two SMB shares that I always mount on startup by opening a terminal, typing "sudo mount -a" and typing my password twice.

How can I automate this so it happens automatically on startup?

---

### Post by Samy_Merchi on 2006-06-03
There's no way to automate it so that it executes "sudo mount -a" on every startup?

---

### Post by catlett on 2006-06-03
[http://www.mepis.org/node/316](http://www.mepis.org/node/316) Mepis is based on debian like ubuntu so hopefuly this will work. When you get to the thread scroll down a few posts. The thread starter answers his own post and gives an explanation of how he edited his /etc/fstab to mount samba shares at start up

---

