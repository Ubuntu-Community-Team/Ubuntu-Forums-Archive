---
title: "What type of server?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by koclea on 2007-04-24
Hi, I've just purchased a Dell Poweredge 2650 server. My first question is "Is there a version of Ubuntu which will run on this hardware?

---

### Post by leg on 2007-04-24
More than likely. Not sure whether the Dell is a x86 or x86_64 platform but whichever it is use the appropriate install disk.

---

### Post by koclea on 2007-04-24
The server initially, will be for authentication of user logons and a file server.  How will my windows clients connect to the ubuntu server?

---

### Post by leg on 2007-04-24
I was looking into this earlier. I haven't tried it yet but you can use samba with winbind to do that. I found some great [info]("http://www.hep.phy.cam.ac.uk/samba-3.0.9/index.html") about samba.

---

### Post by Zuph on 2007-04-24
Ubuntu Server will work fine on this machine, especially if you're a linux beginner.  Apt is an absolute dream to use in a server environment.

Samba will do what you want, and there is extensive support out there for it.

---

