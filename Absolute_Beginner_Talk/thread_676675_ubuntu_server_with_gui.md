---
title: "ubuntu server with gui ?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by NapsterX on 2008-01-24
if i install ubuntu server and i and run sudo apt-get install ubuntu-desktop will it keep the server and just add the gui interface?

---

### Post by Warren Watts on 2008-01-24
yes.

I am running a similar setup myself.

And you don't have to be logged into X for the server to function either.  It will happily sit at the GDM login and serve it's little heart out.

---

### Post by macogw on 2008-01-24
And if you don't want to waste cycles and memory keeping GDM running all the time, you can stop it when you're done with it like this:```
sudo /etc/init.d/gdm stop
``` and then when you want to use the GUI and do your stuff, start it up again like this: ```
sudo /etc/init.d/gdm start
```

---

### Post by NapsterX on 2008-01-24
cool thx

---

### Post by azhamjp on 2008-01-24
apt-get install ubuntu-desktop will install the default gnome desktop just like from the main ubuntu distribution. if u already have servers installed, nothing will be changed there.

---

### Post by hyper_ch on 2008-01-24
what do you want/need a gui for anyway on a server?

---

### Post by NapsterX on 2008-01-24
for an interface, so i can still use the computer for other things, even though most of the time it will be a server

---

### Post by hyper_ch on 2008-01-24
ok :) so you don't want a gui for configuring the server ;)

---

