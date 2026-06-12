---
title: "Deactivate firewall"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-10-28
hi Im currently trying to mount a directory on my client using this command

```
mount -t nfs 146.230.193.109:/nfsshare /mnt/nfs
```

but I get the error mount: RPC: timed out 

I'm trying to check if my firewall is deactivated how do I do that????

---

### Post by Bigbluecat on 2006-10-28
You could try installing Firestarter or Guarddog.

Both of these are graphical front ends for iptables (the built in firewall).

The both give the option to turn off the firewall if you want to or open specific ports.

I use Guarddog but it is the more restrictive. By default if blocks everything. You have to specifically tell it all the protocols to allow (even HTTP).

Firestarter seems to be what most people use if they want a GUI front end.

EDIT: Forgot to add that I think the firewall is enabled by default.

---

### Post by David_T on 2006-10-28
If you have a firewall on that uses iptables, you can find out if iptables is empty by running sudo iptables --list.  If there is something in iptables, you can run sudo iptables --flush to empty it out.

---

