---
title: "[SOLVED] SSH connection problems"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-02-28
II am trying to connect to my new Linode server (Ubuntu 7.10) from my Ubuntu Gutsy desktop. (I can connect from Win XP running in a virtual machine using TeraTerm -- but only if I connect to the LISH console.) I can't get any connection from my Ubuntu desktop.

Here are the errors:

ssh me@117.94.87.28
ssh_exchange_identification: Connection closed by remote host

/etc/var/auth.log shows:
sshd[...] refused connect from [my address]

When using Nautilus to connect to server, I get "i/o error"

The Ubuntu server at Linode.com has deny hosts setup, if that matters.

Any ideas? Thanks.

---

### Post by MountainX on 2008-02-28
solved - my IP address was getting added to hosts.deny on the very first login attempt. Not sure why. For now, I just added my IP address to hosts.allow and I could connect.

---

