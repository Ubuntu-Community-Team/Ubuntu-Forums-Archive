---
title: "Linux, SSH, Putty, etc. How to?"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Cafwin on 2006-06-17
I'll try to keep this short and sweet. I've done what I'm asking about before, just can't remember how. :-( 

I have a copy of Putty on my flash drive. I have my IP (externally?) by going to WhatismyIP dot com. I'm vaguely familiar with setting up the port to connect through the firewall. I'm also somewhat familiar with SSH and creating the tunnel.

(This is all to connect to this system from work to bypass Websense and avoid internet time monitoring.) Using XP Pro from work. I have Mobile Firefox. I seem to have everything I need.

Heck, I know I do because I connect through two colleague's servers.

What I'm hoping to find is a step-by-step on how to set my system, booted to Ubuntu each morning, to accept a connection from work.

I think I may need to reconfig the router as it was reset a few times since the last time I set it up and it worked. So anything with more detail than needed would be great.

Thanks in advance.

---

### Post by mlind on 2006-06-17
Basically, you just need to install package called **ssh**, which will provide
OpenSSH server and ssh client for your Ubuntu box. OpenSSH server will be started
and on daemon mode automatically, so no need to worry about that.

```

sudo aptitude install ssh

```


Then you need to open/forward port for SSH (default is 22) from your firewal/router.
Wiki has instruction about this on [https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

SSH has ability even to forward Xserver connections, so you can use desktop
software remotedly and securely.

---

