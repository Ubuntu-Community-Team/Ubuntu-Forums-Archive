---
title: "firewall question"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by new_foo on 2006-09-30
I've read many posts here about firewall setup and many have suggested using firestarter.  Indeed, I've loaded up several others and played with them, but I have kept firestarter since it is so simple.

Perhaps this is just a well deserved paranoia carried over from xp, but is there a way to monitor programs making outgoing connections?  Perhaps in this environment it's not so important, but with windows xp, my zone alarm sure earned its keep.

Thanks in advance

---

### Post by David_T on 2006-09-30
I'm pretty sure you can use firestarter to deny outbound connections by default, and say which ones you want to allow.  I know you can put something in iptables using the "owner" module to filter output by process ID, user ID of the process, etc.  Firestarter is a front-end for iptables.

---

### Post by xpod on 2006-09-30
Cant you do that with firestarter??
Is`nt monitoring what ports and what ip addresses your using just the same?
Well just as good???
Still learning myself unfortunately.....sorry...fortunately:mrgreen:

---

### Post by orb9220 on 2006-09-30
Well actually firestarter is just the gui frontend for iptables which is installed by default. And side note you don't need to run firestarter on startup only when you need to make changes to iptaples.

But the eastiest way I can think of is to load synaptic. And use different search terms firewall,monitor,network,etc... as individual terms and see what pops up.

And click on each and read the descriptions for programs. 
I am sure there is apps for that sorry I don't know myself.

---

### Post by xpod on 2006-09-30
I know FS is just the front of iptables i just meant like he could monitor stuff from there........easily:D ....

---

### Post by orb9220 on 2006-10-01
> **xpod said:**
> I know FS is just the front of iptables i just meant like he could monitor stuff from there........easily:D ....

Xpod I never seen your post I was talking to him. We must have been posting at the same time,

---

### Post by xpod on 2006-10-01
lol....My humble apoligies.
Usually im missing the posts meant for me so it makes a change.

---

