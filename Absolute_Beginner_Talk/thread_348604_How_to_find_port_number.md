---
title: "How to find port number"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-01-29
I am having a very difficult time finding my port number on my ubuntu computer. I know the ip address but I am trying to remote connect into my computer via another computer via putty but since I do not know the port number I cannot do it. I thus cannot connect remotely to my computer. I am trying to use ssh but it is not working and it requires me knowing my port number. I tried the obvious 20, 21, 22 but none of those work.

I would greatly appreciate if you could tell me how to find my port number. Please either leave a response on the forums or email me at [email]jprb85@gmail.com[/email]

Thank you.

---

### Post by featherking on 2007-01-29
in order to ssh you have to set up an ssh server and an ssh client, the computer set up as the server will have a configuration file that has the port in it. If you are set up properly type this in the terminal to see the configuration file i was talking about

```
cat /etc/ssh/sshd_config

```

Towards the top of that file it mentions what port the ssh server is listening on

---

