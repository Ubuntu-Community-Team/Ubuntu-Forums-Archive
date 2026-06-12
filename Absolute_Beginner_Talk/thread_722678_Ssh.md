---
title: "Ssh"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by tomsyco on 2008-03-12
I cant get ssh t work its installed and i try to access it and i get

tom@UbuntuServer:~$ ssh tom@(MY_IP)
ssh: connect to host(My IP) port 22: Connection refused

Whats going on I had it installed and it worked before and then i reinstalled cant get it to work again. I've also made sure that port 22 is open so i don't get it.

---

### Post by nrs on 2008-03-12
You're sure the SSH daemon is running? 
sudo invoke-rc.d sshd status

also don't you need use -l for the login name?

---

### Post by tomsyco on 2008-03-12
i just logged in using my local ip adress so i think it may be my router or isp or something idk.

---

### Post by nrs on 2008-03-12
I've never heard of an ISP blocking 22, you can try changing the port in /etc/ssh/sshd_config though and restarting the daemon, also making sure the port is forwarded in the router.

---

### Post by jken146 on 2008-03-12
You need to install **openssh-server** on the box you're trying to connect to, if I remember correctly.

---

### Post by Rocket2DMn on 2008-03-12
I believe the correct command is
```
ssh ip[:port] -l username
``` (that's a lowercase L).  the port should not be necessary since 22 is the default for SSH.

---

### Post by tomsyco on 2008-03-12
Here is my router what do i do i tried to set it its not working i this i set the starting ip adress wrond and whatnot.

---

### Post by Iowan on 2008-03-12
My SSH session starts ```
 ssh -p 1234 user@host
```
That's pretty much like yours - but with the nonstandard port called out.

---

### Post by tomsyco on 2008-03-12
Ok so i disconnected my router and went right to my moden and hey it works i hate routers can anyone walk me throught setting this up I have a D-link router.

---

### Post by tomsyco on 2008-03-12
tinkered with the router and now it works.. thanks for the help..:lolflag:

---

