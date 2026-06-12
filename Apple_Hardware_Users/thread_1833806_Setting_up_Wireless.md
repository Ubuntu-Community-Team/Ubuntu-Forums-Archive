---
title: "Setting up Wireless?"
date: 2011-08-26
forum: Apple Hardware Users
---

### Post by brm4620 on 2011-08-26
How do I go about setting up wireless using Ubuntu on a Macbook Pro? I'm so new to this that I can't even figure out what kind of card I'm using!

---

### Post by lael on 2011-08-26
What version of Macbook Pro do you have?

There is some good info that you definitely need to read:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Once you figure out which version you have, most of the wiki pages will detail how to setup wireless for your version.

This is what I do to figure out my wireless card:
```
$ lspci  | grep 802.11
03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
```

---

### Post by brm4620 on 2011-08-26
I have a Macbook Pro 13" from mid 2009. That command doesn't work for me for some reason...

---

