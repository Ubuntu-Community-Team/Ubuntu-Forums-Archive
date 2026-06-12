---
title: "Disable processor scaling? / Feisty 7.04, iBook PPC 500MHz"
date: 2007-12-19
forum: Apple PPC Users
---

### Post by GVCarroll on 2007-12-19
Hi all.

I'm a long time Mac user, just starting with Ubuntu Feisty on my iBook 500Mhx PPC. Although I've messed around with Linux before this is my first attempt to really use it on my own machine.

I'm very happy with my install so far, I have it set up as a dual OSX/Ubuntu 7.04 with all the updates, and it works quite well, except that I've noticed that the CPU cycles frequently between 400MHz and 500MHz settings, maybe every 20 secs with average use.

In any case, whenever it happens, the system and the cursor hitches a bit (the cursor will freeze for a split second and then move again), and it is really annoying. It's about the only problem I have with the install.

My question is: Is there any way to disable this and either have the system run at 400MHz or 500MHz (preferably) all the time? If not, can the cycling be made to slow down, i.e. if the system needs less resources after 1 min it cycles down instead of after, say 5 sec. (or whatever the default setting is)?

Thanks in advance, this forum has been really helpful getting me started, this is about my last major issue, any help (even if it's "can't be done") would be appreciated.

(Also, keep in mind that I'm a Linux noob, I can do terminal basics but I'm no master, thx)

---

### Post by GVCarroll on 2007-12-19
nvm, found it:
apt-get remove powernowd

---

