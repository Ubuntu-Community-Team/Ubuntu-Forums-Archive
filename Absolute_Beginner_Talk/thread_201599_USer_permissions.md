---
title: "USer permissions"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Justgeek on 2006-06-22
Hi :)

I need to set up alot of computers with the same setting.

The system needs to run 2 users:

1. Admin
2. Public user

The public user should only be able to use Firefox browser, and should only be able to browse [http://www.bodyplanning.dk](http://www.bodyplanning.dk). And nothing else.

How do I do this... In newbie language

---

### Post by nalmeth on 2006-06-22
Start at:
SYSTEM --> ADMINISTRATION --> USER'S

I think? Been a while since in Gnome, too long

---

### Post by Justgeek on 2006-06-22
Yea, got a user created, its just setting the User, for only being able to just use firefox, with that specific domain

---

### Post by nalmeth on 2006-06-22
Sorry, its
SYSTEM --> ADMINISTRATION --> USER'S and GROUPS

Click on the user you created, go to 'Properties', click on the 'User Priviledges' tab, and from there you can limit what the user is able to do to a fair extent. Never needed to do it myself.

I don't know much about blocking websites, maybe it can be configured in firefox, or perhaps a firewall could do that. Firestarter and Guarddog are graphical frontends to the iptables firewall already built into Ubuntu.

I know I've run into things like parental controls, but don't have any links ATM. I'll try to dig one up, will post if I find it.

---

### Post by nalmeth on 2006-06-22
[http://dansguardian.org/](http://dansguardian.org/)
Perhaps that will work?

---

### Post by Justgeek on 2006-06-22
Well then I would have to write basicly all of the www adresses in the BAN list, wouldn't I?

---

### Post by Justgeek on 2006-06-26
Any one?

---

### Post by aysiu on 2006-06-26
Read the Synaptic Package Manager description for *dansguardian*.

---

