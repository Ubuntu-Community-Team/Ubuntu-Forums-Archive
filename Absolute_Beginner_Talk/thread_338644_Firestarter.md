---
title: "Firestarter"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by yosarian on 2007-01-14
I have the Ubuntu 6.10 and I installed some time ago the Firestarter (firewall). 
When I turn on the linux I have to turn on the firrestarter manually, is there any way to program the firestarter to starts after linux starts automatically?

Thanks

---

### Post by meng on 2007-01-14
Just to let you know, firestarter doesn't need to be running for your firewall to be active. Firestarter EDITS your firewall settings.

---

### Post by Hankers on 2007-01-14
As mentioned above:

Firestarter is just a graphical interface for configuring the built-in firewall that runs whenever Ubuntu is started.  You don't need to open Firestarter after you have configured it.

---

### Post by yosarian on 2007-01-14
Thanks to both of you, it's good to know that I did have a firewall running all time

---

### Post by Mis_Uszatek on 2007-01-16
Ok - Firestarter - gui for built in firewall.
but...
Could  you tell me which processes are responsible for firewall itself?
And is there any man page about it, or command line for configuration not through gui but from terminal?

---

### Post by davebgimp on 2007-01-16
Linux uses IPTables for its firewall.

[http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[http://en.wikipedia.org/wiki/Netfilter](http://en.wikipedia.org/wiki/Netfilter)

for cli configuration, I much prefer to use Shorewall to manage IPTables for me. Makes life a lot easier.

---

