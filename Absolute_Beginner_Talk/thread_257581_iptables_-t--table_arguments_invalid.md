---
title: "iptables: -t/--table arguments invalid"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Xaiter on 2006-09-14
First of all, I'd like to introduce myself.  I'm bored, installed Ubuntu as my second foray into the world of Linux.  Might as well do something educational with my time.

But, straight to the point.  I'm trying to set up a this little Ubuntu box to do basic NAT stuff, just to get the hang of it.  So far, only very basic arguments seem to work.  append, delete, flush, etc.  But, for some reason, neither of the table arguments seem to work.  Blazes if I know.

---

### Post by Randomskk on 2006-09-14
What command are you using with iptables?
If I try plain -t, I get:
```
adam@wizard:~$ iptables -t
iptables v1.3.3: Unknown arg `-t'
```

However, with a table name:
```
adam@wizard:~$ iptables -t NAT
iptables v1.3.3: no command specified
```

---

### Post by steve.horsley on 2006-09-14
I think you need to be more specific - post the exact command you are trying and the result you get/expect.

Here is an example of using basic table selection (the table selection must come first, according to the manual)
> root@dingly:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@dingly:~# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


---

