---
title: "script to open multiple ssh sessions"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-02-12
I need to write a script that will automatically connect (SSH) into several machines.  The problem I encounter is that whenever I try to open a ssh connection it doesn't work. also I need a script that will open more then one connection.

Essentially i have 6 client machines and one server, when I turn the server on I am trying to have the server setup reverse port forwarding from each client to the server.

any help on this would be great!

---

### Post by Dr Small on 2008-02-12
What exactly do you mean, it doesn't work?

---

### Post by neurostu on 2008-02-12
Ok well it works, but I can't get the script to fork (&) correctly so I can open multiple ssh sessions simultaneously.

---

### Post by neurostu on 2008-02-12
I already have a script that will setup one SSH session, but if I try to set up another SSH connection in the same script it never happens.

---

### Post by jordanmthomas on 2008-02-12
Are you opening these connections in new terminals or are you just connecting and not doing anything with it?

---

### Post by neurostu on 2008-02-12
Ideally I would like to run all the scripts in the same terminal, but it is looking more and more like I will have to open an individual terminal for each SSH connection.  

So once I have the SSH connection open I don't use it directly (I have some reverse port forwarding setup) but there are applications that use the SSH connection to communicate securely.

---

### Post by neurostu on 2008-02-13
*bump

Anybody?

---

