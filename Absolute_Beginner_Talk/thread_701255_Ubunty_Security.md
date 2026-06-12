---
title: "Ubunty Security"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-02-19
I installed Ubuntu on sunday. I ****love it.
I have a question on my mind right now which is:

How does Ubuntu handle ports? A related question is: Does Ubuntu use a firewall by default, or am I completely clueless, and ports are not used specifically?

---

### Post by njparton on 2008-02-19
All ports are closed by default after install and only opened when needed.

The default inbuilt firewall is called "iptables".  There's a GUI in the repositories called firestarter to administer it.

And careful with the language :)

---

### Post by p_quarles on 2008-02-19
A good discussion of security in Ubuntu/Linux is here:
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by hungryOrb on 2008-02-19
> **njparton said:**
> All ports are closed by default after install and only opened when needed.

The default inbuilt firewall is called "iptables".  There's a GUI in the repositories called firestarter to administer it.

And careful with the language :)

Thankyou very much :] I assume port forwarding is the usual simple matter. I'll check it out anyways and have a play. I didn't mean anything bad by the language, quite the opposite. But I got a warning so I guess I shan't use it again :D

---

### Post by erm4gh on 2008-02-19
How come iptables doesn't show up in the system monitor application? What sort of process monitor software would show it?

I used a cheap router with a built-in SPI firewall and had thought iptables didn't run by default until I verified it using sudo iptables -L . Is there any reason why I should not disable iptables?

---

### Post by tribaal on 2008-02-19
It doesn't show up as a process because it's built-in the kernel.

Using "sudo iptables -L" should give you relevant output...

- Trib'

---

