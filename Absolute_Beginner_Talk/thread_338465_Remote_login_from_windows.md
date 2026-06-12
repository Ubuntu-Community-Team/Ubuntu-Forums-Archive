---
title: "Remote login from windows?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Arrowroot on 2007-01-14
Hi.

Been reading a lot about ssh but I can't get it to work.

This is what I want to do:

When I am away I would like to login to my linux computer from windows using either putty or some of windows buildin application. I don't need an GUI, just a shell. With ssh it seems as I need to use a key id or such. I just want to connect, by using my IP or dns-name and then entering a password which is different from my local password when I login locally. But I still want to log in as my standard user. And I don't want to be able to log in as root remotely.
The reason is that I maybe would like to start a new torrent download so it will be ready when I get home or that I just wanna halt my system.
I dont get it! It should be as easy as telnet but secure.

Guess its quite easy but still, I'm a newbie :confused: 

Thanks for your help.

---

### Post by taurus on 2007-01-14
You need to install sshd and have it start when you boot Ubuntu.  Then, it would listen to coming signal when you want to ssh to it from another machine.

---

### Post by Arrowroot on 2007-01-14
> **taurus said:**
> You need to install sshd and have it start when you boot Ubuntu.  Then, it would listen to coming signal when you want to ssh to it from another machine.

I already have sshd installed. I need help configuring it.

---

### Post by Arrowroot on 2007-01-15
Anyone knows how I should configure it?

---

### Post by dashnak on 2007-01-15
That's weird, I never had to configure mine, just did sudo apt-get install openssh-server....
Now i just connect to [EMAIL="dashnak@my.ip"]dashnak@myip[/EMAIL] and that's it....
It should work out of the box....
Maybe you could open a terminal in your machine and do ssh [EMAIL="username@your.ip"]username@yourip[/EMAIL] and tell us what happens?

---

### Post by Arrowroot on 2007-01-15
I think I got it to work now. The problem seemed to be in iptables.

---

