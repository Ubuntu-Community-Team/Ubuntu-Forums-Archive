---
title: "proxy server?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-07-20
Hi, 

Small issue. My wife's company wont allow her to browse google calendar! Our schedules are not in sync and our lives are going to ruin.

Rather than use some shonky web proxy I was hoping to set one up at home and limit it with some sort of secure access.

A: What am I after? is it a proxy server?

B: What is the simplest (low processor/ low fuss) proxy to install? Squid?

Many thanks.

c.

---

### Post by kidders on 2007-07-21
Hi there,

The answers to your questions are "Yep" and "Yep". :-) You should limit the hosts squid is willing to serve to your wife's public IP though, and if possible (it probably *won't* be), run it on a non-standard port.

One thing worth noting about doing this sort of thing though, is that it may be illegal, or a violation of your wife's employment contract. You should check your local legislation ... here in Ireland, for instance, a person could be summarily dismissed, and charged with a variety of crimes, for circumventing his employer's network restrictions.

---

### Post by Al3xK3aton on 2007-07-21
Any company that can block Google Calandars can also block a proxy. I suggest giving up.

---

### Post by Malibu Illusion on 2007-07-21
^ lol

Alright, run an SSHd on your home terminal.  At work, if you're using a Windows box, download an SSH client.  I recommend PuTTY - Google it, please.

PuTTY can be used to dynamically forward a port on the client terminal through your SSH tunnel.  So, for the sake of argument, you could forward port 9000 on your client through the SSH tunnel connection you have established with your home box.

After doing this, you can set up a SOCKS proxy in your browser, and pretty much anything else that supports SOCKS usage, using 127.0.0.1 port: 9000.  This will grant you unrestricted access to the internet as the connection will be being served from your home box via SSH.  Not only a way to bypass firewalls and blocks, but it's also highly encrypted so the traffic cannot be sniffed.

If you're using a Linux box as your client, its as simple as establishing a connection like so:

```
ssh -D9000 ip.address.here
```

Then using port 9000 as your SOCKS proxy as you would in the above example.

Take care.

---

### Post by cnschulz on 2007-07-22
thank you all very much.

will try the ssh option!

:)

c.

---

### Post by kidders on 2007-07-22
It's certainly what I would do. :-) Don't forget _not_ to bind your proxy to any remotely accessible network interface.

---

### Post by AWerner32 on 2007-07-30
assuming i am using a windows box as the client and a linux box as the host. how can or where do i add teh -D9000 in puTTY using that as the ssh client and if i do forward that port in putty will it work the same way?

---

### Post by AWerner32 on 2007-07-30
nevermind i figured it out in putty its under the tunneling tabof SSH. why do you need to forward the port dynamically, why would remote not work. this is just a curiosity thing

---

