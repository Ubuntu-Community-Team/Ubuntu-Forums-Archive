---
title: "Compiling Intel e1000 drivers: *** Linux kernel source not found.  Stop."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Syzzer on 2006-06-25
When I try to compile the Intel e1000 network drivers (for my PRO/1000 PT network card), I get the following error message:
> *** Linux kernel source not found.  Stop.
I'v been searching the internet about what could be the problem and how to solve it. I've found I had te install these packages:
- build-essential
- linux-headers (I'm running Dapper amd64, so linux-headers-2.6.15-23-amd64-generic)
- gcc 3.4

I've also executed the following command to make sure the gcc-3.4 is used:
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc

But even after installing these packages, I keep on getting the same problem. What could be wrong :?

---

### Post by taurus on 2006-06-25
Looks like you need to install both gcc and linux-headers before you can build a driver for your network card...
```

sudo apt-get install build-essential
sudo apt-get install linux-header-386 (or use synaptic to search for it!!!)

```

---

### Post by Syzzer on 2006-06-25
I did install those packages already. The list in my startpost is the list of packags I've installed. All information in the net tells me I should be able to compile drivers now, but I'm still getting the same error message.

I'm running Ubuntu 6.06 Server, so no gui / synaptic available.

---

### Post by taurus on 2006-06-25
Are you sure you have to same header files as your kernel?
```

uname -r

```

---

### Post by Syzzer on 2006-06-25
uname -r tells me:
2.6.15-23-amd64-server

I've installed these sources:
sudo apt-get install linux-headers-2.6.15-23-amd64-generic
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-23-amd64-generic is already the newest version.

Edit:
Aaargh! Just installed linux-headers-2.6.15-23-amd64-server, did not see those before.

Thanx for your help!

---

