---
title: "ssh on ubuntu hoary help"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2006-07-11
Hey,

I installed the ssh server, however I cannot connect through ssh at all over LAN. I currently use a Netcomm nb5plus4 modem router. Is connecting via ssh over lan disallowed on Ubuntu.

Can anyone help?

Thanks In advance,
Kris

---

### Post by Herks on 2006-07-11
Have you tried using:

ssh 0.0.0.0 -l "user"?

Thats what normaly works for me.....

---

### Post by nkhansen on 2006-07-11
Can you connect to ssh locally? If so, maybe it's a firewall issue.

If not, then try to reboot the server, and see if comes on. Alternatively, (I don't know if this works) try doing a 

```
$ sudo /etc/init.d/ssh start
```

or maybe a

```
$ sudo /etc/init.d/ssh restart
```

---

### Post by KrisDwyer on 2006-07-11
Nup, when i tried to connect over the network, i cannot via SSH.

It times out.

---

### Post by KrisDwyer on 2006-07-11
Any help guys?

---

### Post by echo $USER on 2006-07-11
How are you trying to connect like > ssh user@192.168.x.x?

---

### Post by nkhansen on 2006-07-11
> **KrisDwyer said:**
> Nup, when i tried to connect over the network, i cannot via SSH.

It times out.

Yes, but did you tried ssh'ing from the machine running the ssh server (connecting to itself via ssh)?

---

### Post by pbaehr on 2006-07-11
On a relatively unrelated note:

Is there a reason you're still running Hoary? You're two versions behind the latest stable release.

---

### Post by inf0c0m on 2006-07-11
how did you install ubuntu?

and try sshing into the computer from the computer.

---

