---
title: "updates"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by bjhome on 2008-02-26
i am trying to install my updates. i am getting an error message saying failed to fetch and could not connect to 10.0.0.5:8080 (10.0.0.5) - connect (113 No route to host)
can you please tell me what i need to do to install my updates.

---

### Post by Paqman on 2008-02-26
Do you have a working internet connection? If your internet is working, try changing the servers you use (System > Administration > Software Sources > Download from:)

---

### Post by Crafty Kisses on 2008-02-26
> **bjhome said:**
> i am trying to install my updates. i am getting an error message saying failed to fetch and could not connect to 10.0.0.5:8080 (10.0.0.5) - connect (113 No route to host)
can you please tell me what i need to do to install my updates.

Hmmm, sounds like your internet connection isn't working, or your connection is timing out,

---

### Post by bjhome on 2008-02-26
internet connection is working fine . been surfing the net no problem

---

### Post by bjhome on 2008-02-26
what download server do i need to use, there is new zealand server, (thats where i am from) - main server - or other server  ????

---

### Post by PeterJS on 2008-02-26
Looks like a proxy problem 10.x.x.x is a private/local address, and port 8080 is the default port for an http proxy. Have you changed other network settings, moved your machine, or changed or removed a proxy from your network?

---

### Post by oedha on 2008-02-26
go to system - administration - software sources
mark those boxes........main server will be better
close it and reload it
..

---

### Post by PeterJS on 2008-02-26
The proxy settings for synaptic are under Settings > Preferences > Network, you probably want to set that back to direct connection. You might also want to try running:
```

sudo apt-get update

```
Just to see if you also have a proxy set up for the command line tools. I hope not that's more of a pain to take care of.

---

