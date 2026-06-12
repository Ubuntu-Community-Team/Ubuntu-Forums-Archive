---
title: "Opening Ports"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by sunrex on 2006-11-26
How do I open ports on a server only install?

I'm asking this because I think ubuntu is blocking the ports i need - 9180/9181

Thanks!

Sunrex.

---

### Post by NetworkGuy on 2006-11-26
By default, Ubuntu does not run any servers, thus ports do not respond.  Unless you have configured IPTables on your server, loading what you want on your server should open the ports you need.

What are you trying to access?

---

### Post by sunrex on 2006-11-26
its a script that will receive logs from my Gmod server - a hl2 based mod, and send the logs to my webserver, which is not hosted on my ubuntu box, and then when the client logs on they can see the logs - its a web based rcon website.

---

### Post by sunrex on 2006-11-27
bump

---

### Post by steve.horsley on 2006-11-27
Well, if it's a script that listens on those two ports for incoming calls, run that script and it should open the ports. You open ports by running something that opens and listens on those ports. Ports are only closed because there is nothing listening.

---

