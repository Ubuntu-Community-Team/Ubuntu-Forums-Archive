---
title: "Wil someone check if this ssh port is working?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-01
I can ssh out to another ssh server, and then ssh back, but if I try to ssh directly using putty, theres no luck...

anyways, my daemon is running on .removed.

can someone see if they can get the login to come up?

---

### Post by lespaul_rentals on 2008-02-01
Doesn't work.  Which port are you using?  If you are behind a NAT, did you remember to forward it?

---

### Post by tava0002 on 2008-02-01
I was unable to connect to that address with putty, I get no login prompt.

---

### Post by joesmith1234 on 2008-02-01
Sorry, my network card crapped out... 

can you guys try again?

---

### Post by lespaul_rentals on 2008-02-01
[img]http://www.maj.com/gallery/silverscythe/tripleboot/proof.jpg[/img]

It works!  :D :D :D

Just a tip, you might want to edit your configuration file to not allow root logins. ;)

---

### Post by joesmith1234 on 2008-02-01
thanks.  i wonder why i cant ssh to myself??  :-/  router i guess...

---

### Post by lespaul_rentals on 2008-02-01
NATs will not allow you to access your public IP address from a private IP address within the network.

---

