---
title: "[SOLVED] how to verify if something is installed and running... help"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by goldencj on 2007-12-29
How do I verify the mysql-server is installed and running?

---

### Post by clayts450 on 2007-12-29
System->Preferences->Sessions

Under the Current Sessions tab it should tell you what is currently running

Alternatively type top into the Terminal (Applications->Accessories->Terminal) and you can see all processes running there

THis is what I use anyway - I'm a noob too ;)

---

### Post by jflaker on 2007-12-29
go into Synaptic (System>>Administration>>Synaptic Package Manager) and search for and download mysql-admin

you can look at the service through the gui and change and adjust the server.

---

### Post by RomeReactor on 2007-12-29
Hi. You could also try:
```
ps -C mysql-server
```
if it returns a PID, then it's running.

---

