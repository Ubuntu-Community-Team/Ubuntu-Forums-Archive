---
title: "2 questions : alias &amp; ssh port"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-07-10
hi,

1.

how do i set alias in console. i want some thing like this : 

bunny=ssh server.something.org

so that when i type in console "bunny" it connects with the server.something.org
and not just with current session but i want it always active

2.
how to change ssh port? i tried editing ssh_config(something like that)
but it won't connect from my win machine no matter what i do (even with port 22 which is default).

and how do i restart te service when i change it's configuration (like in the ssh port question - guide said that i must restart service to take effect but i don't know how)

thnx in advance

---

### Post by jrb114 on 2006-07-10
To alias a server, you need to do:

```

alias bunny="ssh myusername@myserver -Y"

```

Put this in your .bashrc (or your .bash_aliases and check it's uncommented in .bashrc)

```

gedit ~/.bashrc

```

And it'll set up every time you open a terminal.

If you tack on -Y at the end, it includes X11 forwarding.

If you want to change the SSH port, I guess (not sure as I use the default), that you'll want to uncomment the line in /etc/ssh/sshd_config 

(If you change the port line in ssh_config, this configures /outgoing/ connections, not the daemon that listens for incoming ones.)

```

sudo gedit /etc/ssh/sshd_config

```

Scroll down to the line that says 

```

Port 22

```

and change the port to whatever you want.

Save it. And restart ssh:

```

sudo /etc/init.d/ssh restart

```

N.B. If this doesn't work, you may need to install ssh in the first place.

```

sudo apt-get install ssh

```

Hope this works...

J


== EDIT ==
Oops, I've just read that you're trying to change ssh_config, with no joy. I've now updated this post to say sshd_config, which is what I meant to.

Now, to ssh into the machine

```

ssh username@mymachine -p newportnumber

```

---

### Post by zekopeko on 2006-07-10
thnx. this helped. i still have to try ssh port. so i'll post my findings later

---

