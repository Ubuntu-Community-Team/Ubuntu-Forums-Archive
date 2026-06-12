---
title: "How to connect through ssh from remote site?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by mai52 on 2007-07-08
First of all I want to say I am so excellent to use Ubuntu! I buy a lot of stuff to build a new computer for Ubuntu, and I may be the only few people who use Ubuntu in Hong Kong at this moment lol. 

My question is that I want to connect to my server through ssh from very far away, let's say my office. So it would be using the ip 192.168.x.x to connect. I tried many times and searched for an answer to do this in Ubuntu, but I still cannot do it. I could do it in Fedora or PCLinuxOS. I can connect to my Ubuntu server within local network but not remote location. 

Actually I have set up everything for my router and I have a IP forward service, I just don't know how to open a port for my ssh. I am using the newest 7.04 desktop version of Ubuntu. I change ssh port from 22 to 3333, and try to change the iptable to open the port. Somehow still cannot connect from a remote site. Is there somewhere in ssh control letting what range of IP to connect? Or somewhere in Ubuntu controls the range of IP to connect to the server?  

I have installed both ssh server and client and able to ssh myself through a terminal in my Ubuntu.

Please help! Thanks for your answer!:lolflag:

---

### Post by taurus on 2007-07-08
Looks to me like your home computer is connected through a router, 192.168.x.x.  Therefore, you need to get into your router and open port 22 for incoming traffic.  Then, you need to install openssh-server on your Ubuntu before you can ssh to it from another computer.

---

### Post by steve.horsley on 2007-07-08
192.168.x.x is not a publicly accessible internet address. You must have a router that is performing translation to a public address (e.g. 1.2.3.4). You will need to configure this router to forward incoming calls (to port 22, SSH) to your 192.168.x.x port 22 internal address. And then from outside, you SSH to the router's public address, not the 192.168 address, and the router forwards the call.

Make sure you have strong passwords, or use a firewall to limit who can connect to the SSH server. There are lots of SSH password guessing bots out there that just sit guessing passwords all day every day.

---

### Post by mai52 on 2007-07-08
Thanks for your answer and actually I have set up everything for my router and I have a ip forward service to keep track of my ip, so I know where to find my computer IP even when I am at office. I have opened every ports for my router so everything just goes directly to my Ubuntu server. I just don't know how to open my port in Ubuntu for ssh. It looks like the ssh port is not open yet. I am using the Ubuntu desktop version. Please help and thank you!

---

### Post by taurus on 2007-07-08
Have you installed openssh-server?  You need to install ssh server on your machine first before you can ssh to it.  And by the way, you don't need to open any port on your Ubuntu.

```
sudo aptitude update
sudo aptitude install openssh-server
```

---

### Post by mai52 on 2007-07-08
> **taurus said:**
> Have you installed openssh-server?  You need to install ssh server on your machine first before you can ssh to it.  And by the way, you don't need to open any port on your Ubuntu.

```
sudo aptitude update
sudo aptitude install openssh-server
```

Yes I have installed both openssh-client and server, and I can connect to myself through a terminal in my computer.

---

### Post by taurus on 2007-07-08
Have you tried to reboot?  What's the output of this command from a terminal?

```
ps -A
```

p.s.  What do you get when you try to ssh to your home machine from work?

---

### Post by mai52 on 2007-07-09
> **taurus said:**
> Have you tried to reboot?  What's the output of this command from a terminal?

```
ps -A
```

p.s.  What do you get when you try to ssh to your home machine from work?

I am in my office now so I cannot try the command yet.

When I do "ssh (my ip)", it doesn't have reaction and seems like cannot connect to my computer at home.

Does the default setting of Ubuntu ssh server let a user ssh from remote site like office? This is what I wonder now.

---

### Post by mai52 on 2007-07-09
Hello can anyone help me who is from Hong Kong? Help!:KS

---

### Post by mai52 on 2007-07-09
so no one how to do this? The simple ssh setup!? So why so many people use the forum if no one can solve such a simple question?:confused:

---

### Post by hyper_ch on 2007-07-09
maybe ssh is blocked at your work...

---

