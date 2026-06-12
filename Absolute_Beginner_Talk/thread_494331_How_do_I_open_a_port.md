---
title: "How do I open a port?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by David8 on 2007-07-06
I just installed Feisty server 7.04 (command line only, no GUI) and PostgreSQL.  I need to open port 5432 for sql connections.  How do I do this?  What is the correct command line tool?  How do I check for open ports?

---

### Post by Rocket2DMn on 2007-07-06
Ubuntu doesn't have a firewall exactly, it uses iptables to make the correct ports available for running processes.
If you are behind a router, THIS is where you need to open a port, which means you need to enable port forwarding.  Every router is different, so you either need to look up on your router manufacturer's website about how to port forward on your model router, or let us know and perhaps somebody has used your router before and can help you on the spot.
Typically you login to your router using a web interface and are able to navigate the configuration, it should be relatively self-explanatory.  Linksys keeps their port forwarding under the Games and Applications tab (or something similar).

---

### Post by robertc36 on 2007-07-06
You should be looking for something like firewall rules / services etc.. but mayye you know that anyway.
Still you add the service and then set the firewall rule for it- simple.

---

### Post by por100pre1 on 2007-07-06
If you want some control over your traffic use Firestarter, it's an easy GUI for iptables and will give you some extra security too.

---

