---
title: "I need help with Telnet"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by jimmy85 on 2007-01-31
Hy guys! I have a problem with the application Telnet.
Can you help me?
How to use Telnet on my Ubuntu Linux??
What is the comand?
Have I install previously any package or something?
Thanks.

---

### Post by PetePete on 2007-01-31
telnet hostname port

eg
telnet google.com 80

if it doesn't recognise command telnet, then you prob need to install it
sudo apt-get install telnet

---

### Post by taurus on 2007-01-31
Instead of using telnet, try using ssh.  If you want others to connect to your machine, then you need to install sshd (openssh-server) but if you want to connect to another machine, then you use the ssh (client).

```
ssh -l **username** IP_of_other_machine
```

And to install sshd on your machine so others can log in over the net, do

```
sudo aptitude update
sudo aptitude install openssh-server
```

---

### Post by jimmy85 on 2007-01-31
This is my problem:

jaume@labxarxes11:~$ telnet 172.28.1.11 80
Trying 172.28.1.11...
telnet: Unable to connect to remote host: Connection refused

I can't connect with another PC unless they are connected by ethernet hub.
I don't know why?

---

