---
title: "A very simple Samba server"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by mjwhitfield on 2007-07-11
Hello all,

I'm getting an old PC from a friend which I plan to use as a Samba server.  I want the most light weight install I can have on it, to maximise performance and disk space, so I figured I'd use the minimalCD.  Once it's installed I will of course have to apt-get all the packages I need.  It's only going to have a monitor and keyboard plugged in for the very first install, so I'll need to be able to SSH into it.

So my question is this... what packages will I need to apt-get to install the samba components and the SSH components?  Also, are there any other packages that I'll need which I'm overlooking? Also, how do I set a static IP for the box from the command line?

Many thanks!

---

### Post by scxtt on 2007-07-11
**sudo aptitude install samba** should get you the minimal components necessary for samba
**sudo aptitude install openssh-server** should square away SSH

sudo vi /etc/network/interfaces
```
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
```should set up static IP - depends on your network of course ...

---

### Post by hyper_ch on 2007-07-11
Well, I'd use the server CD and not install any servers...
Then I would just install openssh-server and samba:

```

sudo aptitude install openssh-server samba

```

To set a static IP you need to edit two files:

/etc/network/interfaces
```

iface eth0 inet static
address 10.0.0.5
netmask 255.255.255.0
gateway 10.0.0.1

```
--> In the above case, 10.0.0.5 is the IP of the machine and 10.0.0.1 is the IP of the router

Then you also need to edit the /etc/resolv.conf
```

nameserver 10.0.0.1

```
Set as nameserver IP the IP of your router

That should do it for I think for the static IP

---

### Post by mjwhitfield on 2007-07-11
do i need the smbfs package?

---

### Post by hyper_ch on 2007-07-11
How are we supposed to know what you need? Google for it, read up what it does and then decide wheter you need it :)

---

### Post by mjwhitfield on 2007-07-11
I would do, but I haven't found a howto for making a samba server from the mini install.  So I have no idea what underlaying packages I would be missing that I would need.

---

### Post by b20963a2 on 2007-07-11
Why no try something like freenas or openfiler?

---

### Post by mjwhitfield on 2007-07-11
> **b20963a2 said:**
> Why no try something like freenas or openfiler?Simply because one day I might want to put a desktop on it, or something else.  I like the idea of the ubuntu mini as it gives me a great base to start from, and I understand parts of it already.

---

### Post by scxtt on 2007-07-11
if smbfs is needed by samba, it'll resolve that dependency automatically ... you should only **need** smbfs for some specific cases (not to "map network drive" and browse shares in windows/linux) ...

---

