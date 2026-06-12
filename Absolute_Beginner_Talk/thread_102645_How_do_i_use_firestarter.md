---
title: "How do i use firestarter?"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by luap on 2005-12-12
I went on synaptic and downloaded firestarter.. now what.. i cant find a shortcut to firestarter.. do i still have to type something in the terminal?

---

### Post by lutrafobic on 2005-12-12
try:  
```

sudo firestarter 
```
at the terminal.
The first time you start firestarter it will walk you though a nice guide. Then the firestarter will be started 'quietly' in the background at all times. And if you want to configure it you start it with the code from above.

---

### Post by luap on 2005-12-12
ok so when i exit the terminal and firestarter, it is still running?

---

### Post by lutrafobic on 2005-12-12
Yes it is.

You (usually) only start the GUI when you want to change configuration.

---

### Post by ninotob on 2005-12-12
[QUOTE=luap]ok so when i exit the terminal and firestarter, it is still running?[/QUOTE]

Yes it is.  Firestarter basically uses iptables, the linux firewall, but gives you a nice gui front end.  After you set up firestarter, the firewall runs as you configged it even if you close the firestarter window.  The firestarter window exists to provide you an easy way to config iptables, and if you keep it open, to show you current information regarding your network.

Firestarter has a small manual you may want to check out:
[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

As for the menu icon -- sometimes you have to logout and log back in for them to show up.  It should be located in the Applications-System Tools menu.

EDIT:  BTW, if you launch from the terminal and want firestarter (or any program) to stay open even if you close the terminal, append " &" to the command.  For example:

sudo firestarter &

You can then close the terminal and the firestarter window will stay open.

---

### Post by luap on 2005-12-12
Thanks for the help..

I installed Java (atleast that's what i think)..

I was wondering how to tell if i installed java correctly.. can i open it cuz again i couldnt find a shortcut .. thanks

this is is my first day with it.. lol sorry

---

### Post by jwd45244 on 2005-12-12
An even better questin is: Do I need to use Firestarter?

Out of the box, as a desktop (not a server) Ubuntu does not run applications with open ports.  Linux does not need a separate "firewall". The capability is built into the networking part of the Linux Kernel.

IN order to change the rules as to what kinds of packets you might want to let in, you need to use iptables.  Firestarter is just a pretty face on iptables.

---

### Post by ninotob on 2005-12-12
I would say that even if one has no ports open *now*, it does no harm to run firestarter/iptables.  Not that it will make any difference right now ... but say in the future the user installs something that does open a port and doesn't think about firewalling -- then it can make a difference.  I think it's a reasonable idea to get used to working with a firewall even if it isn't exactly necessary.

---

