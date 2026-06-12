---
title: "Can't install on server with Compaq Smart Array"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by getut on 2007-02-05
I am trying to install Ubuntu Edgy to an old Compaq Proliant CL380 server. This is the Compaq clustering server but I'm only using a single node as a standalone machine.

Ubuntu seems to be having difficulty with the Compaq Smart Array controller in this machine. It always detects as /dev/ida/c0d0 - 0B0 Compaq Smart Array and cannot partition the drives.

I found a previous thread mentioning that certain kernels had problems with that array controller. I tried the Edgy alternate CD as well as the Feisty Herd 3 alternate CD. All have the same problems.

Can anyone help me with this? I'd rather get Edgy put on there if possible.

---

### Post by CaptSaltyJack on 2007-04-09
Same problem here.  Can't even mount /dev/ida/c0d0 as a directory.. so I can't install Ubuntu 6.10 on this server.

Anyone have any solutions for this?

---

### Post by CaptSaltyJack on 2007-04-09
Nevermind, tried Ubuntu 6.10 Server instead of the standard desktop version.. works great!

---

