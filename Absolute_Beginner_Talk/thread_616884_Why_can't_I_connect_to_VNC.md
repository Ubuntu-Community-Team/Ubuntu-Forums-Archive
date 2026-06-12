---
title: "Why can't I connect to VNC?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-11-18
If I login in graphically on the host system, then I can use vncviewer and control the desktop.

However I want to be able to start the vnc from the command login and have resumable sessions.

I run vncserver, and it returns that the new X desktop is host:1

On the client computer I try to connecting with vncviewer host:1 but it gives me an error: Connection refused (111).  What does that mean?

---

### Post by rax_m on 2007-11-20
I haven't really tried this myself, but an obvious question is have you allowed the client computer to get to the host computer? 
I think by default Ubuntu doesn't allow any incoming connections and I use something like firestarter to allow a particular client to connect to the host.

---

### Post by AncientPC on 2007-11-21
I haven't installed any 3rd party firewall (like firestarter) or configured iptables at all.  When I've installed samba, openssh-server, etc. packages I've never needed to configure iptables at all for them to work.

---

