---
title: "Messed up root account with sudo -i -u"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by acsworrell on 2008-02-29
I just recently changed my entire home over to Gutsy from Microsuck. 5 flawless installs later, I think I might have made a big mistake. On my desktop I ran Sudo -i -u to temporarily act as root. Now the root folder shows me as the owner and shows my home folder as root being the owner. How do I fix this? Everything still works correctly. Should I be concerned with this?

---

### Post by neurostu on 2008-02-29
Is that the only command you ran?  Also have you tried restarting?

---

### Post by justleen on 2008-02-29
your /home/<username? hould not be owned by root..


if you sudo -i , your "home" changes to root, which is owned by root..

its all temporary, so an "ecit" at the command line brings you back to your user..


as long as you did not change any permissions / ownerships there is nothing to worry about..


if the permission on /root  and /home/username ARE wrong, fix it like this:
```

sudo -i
chown -R <username>:<username> /home/<username>
chown -R root:root /root

```
which does:
chown changes ownership, 
-R for  recursivly,
owner:group 
path to change ownership of..

---

### Post by acsworrell on 2008-02-29
neurostu: I did restart and had the same problem, but you were right, I did run something else as well. justleen: Your directions put everything back in order. Thank you both for you help and fast response.

---

