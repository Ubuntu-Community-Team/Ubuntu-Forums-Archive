---
title: "ssh/scp problem"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by 404abc on 2006-05-17
I have an Ubuntu linux box and I can't ssh or scp into it.

It seems these services are being blocked.  How do I unblock them?

I looked all over the user interface trying to figure it out and couldn't.

Thank you.

---

### Post by lnxpwr on 2006-05-17
are you sure the ssh-package is installed (sudo apt-get install openssh-server) on your box ?

---

### Post by redistributer on 2006-05-17
You can check in the gui by going to System ---> Administration ---> Services  
Make sure remote shell server is in the list and the box is checked.

---

