---
title: "ventrilo serving help"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by p3ngu1n on 2007-07-23
ok so i am trying to serve ventrilo on my xubuntu computer and everything looks great. it does exactly what its supposed to and it looks like its working. exept one thing. me and everyone else cannot connect. i cant connect from the computer or anything. i got the right ip and all, but its not working.

---

### Post by Ek0nomik on 2007-07-23
Are you behind a firewall?

If you have a router splitting the connections within your household you usually have a firewall built into the router.

---

### Post by p3ngu1n on 2007-07-23
yah i do actually. how do i get arround that? without changing the firewall or watever for the other computers?

---

### Post by Ek0nomik on 2007-07-25
You should open a single port for Ventrilo to run on.

Try following these steps (something similar, as not all routers are the same)

Open your browser and go to:  [http://192.168.1.1](http://192.168.1.1)

Be default, your username should be left blank, and the password will be 'admin'.

Than, look for something called Port Forwarding.

Now, open a terminal and type:

```
ifconfig
```

Note your IP address.  (We want your internal address, not external)  It probably begins with 192.

Make note of the last digit(s).

In the Port Forwarding section, open your port that you have specified in your Ventrilo configuration file, and open it on your IP address.  (Ex:  if ifconfig showed you having an address of 192.168.1.40, then you would want to open your port on that address)

---

