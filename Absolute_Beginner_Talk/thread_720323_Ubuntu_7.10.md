---
title: "Ubuntu 7.10 ?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by jbalazs on 2008-03-10
I run ubuntu 7.10 wen it goes trough 26-30 startup it goes trough a 
system check. Can I run that check in terminal if so what is the command ??
Thanks

---

### Post by Paqman on 2008-03-10
That check is called fsck. You should never run it on any disk partition which is mounted. That's why it's run at startup before mounting your partitions. If you really wanted to run it, boot into a LiveCD and run it from the terminal.

---

### Post by jbalazs on 2008-03-10
Thanks for the fsck. Some time my ubuntu hangs up on something
and I can't singe in at the username and password page, but after the fsck check it's back to normal. Just try to get around a 26 boot up

Thanks

---

