---
title: "xvnc4viewer connection refused error (111)."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2008-01-17
HI 
I have an older computer on which I installed Xubuntu.
When trying to access it from my Ubuntu laptop using Xvnc4viewer I get error message: unable to connect to host connection refused (111).
I also tried accessing it from my windows machine and i get the same error message.
When I use vnc to access my laptop from the Xubuntu box it works, same for accessing my laptop from my windows box and from my laptop to my windows box.

After googling I haven't found much info, other than this is a generic error msg and might have something to do with the ports.

I turned off firestarter, but I still get the same message and I tried editing hosts.allow and hosts.deny, but no change.

Can anybody out here tell me what the problem is and perhaps provide a solution?

greetings

---

### Post by njparton on 2008-01-18
Do you have a vnc server running in xubuntu?

Sounds likeyou have just a client running which will allow you to vnc out of xubuntu, but not allow any other computer to connect to it.

vnc4server I think is the latest version, but I've never really used it.  I rely on vino the default vnc server that's bundled with gnome.

---

### Post by quinnten83 on 2008-01-18
I shouldn't really. I reinstalled vnc4server twice.
Unless the package is broken in Xubuntu.
Do they have a launchpad page, perhaps I can find something on it there.
Google has failed me on this one.

---

### Post by jermor on 2008-03-08
I don't know if you're still having this problem, but I had the same thing happen and the solution was simple:

Instead of trying to connect with
```
xvnc4viewer xxx.xxx.xx.x
```

try this:
```
xvnc4viewer xxx.xxx.xx.x:1
```

Might not help, but it worked for me.

---

### Post by Wobedraggled on 2008-03-10
Mine was working like a charm, then just stopped working.

Gah.

---

