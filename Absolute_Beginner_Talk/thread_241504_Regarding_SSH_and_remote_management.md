---
title: "Regarding SSH and remote management"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Chapmonkey on 2006-08-22
G'day fellow Ubuntians!

I'm in a bit of a pickle here. I have two old PC's that i've decided to test Ubuntu on, but i don't much feel like extra sets of keyboads, monitors etc. Nor do i want a KVM switch.

I was thinking, is it possible to set up these two PC's so there's just a power cable and a network cable connected to them, and then run some sort of SSH connection to remote manage them from a third PC?

Or any alternative suggestion would be welcome as well.

---

### Post by encompass on 2006-08-22
yup... just install the openssh-server
```
sudo apt-get install openssh-server
```
Then you can log into those computers from anywhere jsut type their IP in. At leat locally, get more complicated past the router.
And there are piles things you can do in text mode.  I love most my day in text.  Everything from chatting to mp3 and even cd burning.

---

### Post by edafe on 2006-08-26
Step-by-step instructions on how to use public key authentication with SSH:

[http://www.edafe.org/ubuntu/index.html#authentication](http://www.edafe.org/ubuntu/index.html#authentication)

Regards,
Edafe

---

