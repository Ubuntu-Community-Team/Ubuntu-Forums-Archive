---
title: "boot to terminal"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by rannasjem on 2007-02-15
I messed up X and now can't boot into ubuntu, I get an error that X isn't configured correctly and then startup hangs without kicking back out to a terminal.  Is there a way to start directly into a terminal so I can reconfigure X again?

---

### Post by Tomosaur on 2007-02-15
you should have a recovery mode option when you start up your machine.

Failing that, hit ctrl+alt+f1 when you get the X error, and you should be able to log in via the terminal.

---

### Post by dcstar on 2007-02-15
> **rannasjem said:**
> I messed up X and now can't boot into ubuntu, I get an error that X isn't configured correctly and then startup hangs without kicking back out to a terminal.  Is there a way to start directly into a terminal so I can reconfigure X again?

CTRL-ALT-F1, log in, then:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rannasjem on 2007-02-15
thanx, I didn't know ctr-alt-(f1-f6) worked even when not logged in.

---

### Post by dcstar on 2007-02-15
> **rannasjem said:**
> thanx, I didn't know ctr-alt-(f1-f6) worked even when not logged in.

The door to the Linux world has just opened up a little bit more for you.....   :wink:

---

### Post by Tomosaur on 2007-02-15
> **rannasjem said:**
> thanx, I didn't know ctr-alt-(f1-f6) worked even when not logged in.

Well, now you do :)

---

### Post by bodhi.zazen on 2007-02-15
He he ...

If you think that's cool :

[http://www.ubuntuforums.org/showthread.php?t=271674](http://www.ubuntuforums.org/showthread.php?t=271674)

---

