---
title: "samba - different results different client"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by getut on 2007-03-17
Ok.. I'm gonna have to change my nick to helpjunkie.

I've got samba working on a laptop on my home network but with a weird twist that I cannot seem to resolve.

If I connect to the laptop (\\laptop1\all) from my Windows XP desktop, it properly asks me for my username and password before allowing me ANY access at all. Once I have given the correct username and password, I then have full read/write access. This is exactly the way I want it to work and the way I thought I set it up.

Here is the twist:

When I connect to the same laptop from my OTHER laptop which is running Ubuntu Feisty (smb://laptop1/all), it does NOT prompt me for username and password, but immediately shows me the contents of the share and it is also read only instead of read/write.

What have I done wrong and how can I fix it?

---

### Post by glenndavy on 2007-03-17
Hi 
samba... ahh its been a while... can you attach /etc/samba/smb.conf ?
glenn

---

