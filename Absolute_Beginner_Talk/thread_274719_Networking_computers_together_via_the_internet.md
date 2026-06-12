---
title: "Networking computers together via the internet"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-10-10
Good morning, all.

What would be involved in networking my Ubuntu laptop at work to my Ubuntu desktop pc at home?

I'd like to be able to sync the one at home with the one at work so that, regardless of which office I'm working from, I'll have all of my important files.

Is this doable?

Best,
Tom

---

### Post by hw-tph on 2006-10-10
ssh/scp for secure communication and data transmission, plus rsync for synchronization can work wonders. You pass the *--rsh=ssh* option to rsync to use ssh for secure communication. Read more in the rsync man page (type **man 1 man**).

Håkan

---

