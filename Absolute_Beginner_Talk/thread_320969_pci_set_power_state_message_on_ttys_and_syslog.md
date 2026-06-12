---
title: "pci_set_power_state message on ttys and syslog"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by siman on 2006-12-18
when switching to a virtual terminal (STRG+ALT+Fn) or looking into /var/log/syslog I get a lot of those messages:

```
 Dec 18 15:00:03 silentia kernel: [17194675.788000] pci_set_power_state(): 0000:04:07.0: state=3, current state=5 
```

I took a look at lspci output, and found this:

```
 04:07.0 Ethernet controller: 3Com Corporation 3c900 10BaseT [Boomerang]  
```

My question is two-fold :-)

* is there an easy way to get rid of those messages (they make it impossible to work on ttys)
* can i "fix" the set_power thingy, to work

----

Possibly related: I can suspend / hybernate my PC with no problems - except the network card, which "stops working". What I mean with "stops working": I'm no longer connected to the internet. I can ifdown the interface, but on ifup it just hangs... no error messages in syslog, it just doesnt ifup.

I would greatly appreciate any help... I just recently found out about suspend and hybernate, because vista usually doesn't really shut down, just hybernate - i think this is a great feature, it reduces boot time to 1-3 seconds :-)

---

### Post by siman on 2006-12-19
I found a workaround - when I disable the system monitor in my toolbar, only the network display. those messages are gone. got the tip from here:

[http://groups.google.com/group/linux.debian.user/browse_thread/thread/4cd05212c652bd28/77ba3f1a95cab2cb?lnk=st&q=pci_set_power_state+messages&rnum=6#77ba3f1a95cab2cb](http://groups.google.com/group/linux.debian.user/browse_thread/thread/4cd05212c652bd28/77ba3f1a95cab2cb?lnk=st&q=pci_set_power_state+messages&rnum=6#77ba3f1a95cab2cb)

and maybe this guy is right, and it has something to do with 3com, i got a 3com card too: 

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/192ab72f9939810c/e1f57e6e04317e41?lnk=st&q=pci_set_power_state+3com&rnum=1#e1f57e6e04317e41](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/192ab72f9939810c/e1f57e6e04317e41?lnk=st&q=pci_set_power_state+3com&rnum=1#e1f57e6e04317e41)

I'll start another thread for the suspend-2-ram problem

---

