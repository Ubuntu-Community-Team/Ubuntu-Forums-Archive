---
title: "What scripts are started when you press suspend or hibernate?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by ralphz on 2007-08-24
HI

My question is what scripts are being run when you press suspend or hibernate in Feisty (Gnome)?

I tried to find scripts using sudo find . -name hibe* but there are few different scripts.

PS: How can you find out this kind of things? 

Ralph

---

### Post by picpak on 2007-08-24
I don't know if these are the commands used by Gnome, but they're used for hibernating and waking up:

Sleep: xset dpms force off
Wake Up: xset dpms force on

I don't remember how or where I found these...somewhere on Google, and I've kept them ever since.

---

### Post by jordanmthomas on 2007-08-24
Those are just for the monitor (I have them bound to keys on my keyboard because my screen stays off when I close and open the lid on my laptop)

[http://www.penguin-soft.com/penguin/man/8/hibernate.html](http://www.penguin-soft.com/penguin/man/8/hibernate.html)
I believe the command to hibernate is just the "hibernate" script.
On my system (which is not Ubuntu) it's located at /usr/sbin/hibernate but you should be able to find yours with
```
which hibernate
```

[Here's]("http://gentoo-wiki.com/HOWTO_Software_Suspend_v2") a pretty in depth article on the Gentoo wiki.  Everything should apply to you as well, but you can ignore anything about kernel support (Ubuntu builds it in there)

From what I understand, you also use the hibernate script to suspend.

---

