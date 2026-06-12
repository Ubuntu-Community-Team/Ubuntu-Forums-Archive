---
title: "Samba domain keeps asking for Password"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-03-20
Hi,

I'm running an Ubuntu 7.10 server as a DNS and whenever I try to browse the network in the GUI it asks me to login to my domain. None of my passwords seem to work yet, I can cancel the login window and access shred drives directly. I'm assuming that this is something to do with my user access to the Domain, but I have the same user account and setting on all 3 PC's.

Any ideas what i should be doing to sort this out? Is it a conflict between the bind files and Samba?

Thanks


Mark

---

### Post by sayakb on 2008-03-20
Same problem here and I cannot access anything. Someone told me that its a user permission problem but I couldn't work it out..

---

### Post by jonabyte on 2008-03-20
on the samba box:

```
useradd -c username
```

then 

```
smbpasswd -a username
```

without seeing your conf details, this is the only solution I could come up with for the both of you.

---

