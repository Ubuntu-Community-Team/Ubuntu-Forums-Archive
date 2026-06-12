---
title: "First Time Username and Password"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Robster34 on 2007-06-04
Okay, here's the ultimate newby question even though I have actually used Ubuntu before. I just did a fresh install of Ubuntu 6.10 on my secondary PC and everything went just fine. The problem I am having is that I know that the software asked me for a password during installation, but what is the username for a first time log-on. I remember this plaquing me the first time I installed this program. Eventually, I figured it out but of course I didn't write down my discovery when I did it.

So logging in for the very first time when I haven't even had a chance to setup any users yet. What is the default username and password (or is the password the one I esthablished earlier?)

Thanks in advance,

Rob

---

### Post by taurus on 2007-06-04
If it didn't ask you for a username when you first installed it, then use **oem** as your username.  And after you log in, don't forget to run this command to actually create an account for you to use from now on.

```
sudo oem-config-prepare
```

---

### Post by Robster34 on 2007-06-04
Aha! Hooray! Thank you very much. Now I am in and everything is working good.

I'll be absolutely sure to write that down this time.

Rob

---

