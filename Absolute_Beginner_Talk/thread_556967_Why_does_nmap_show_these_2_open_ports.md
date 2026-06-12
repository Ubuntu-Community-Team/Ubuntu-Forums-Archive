---
title: "Why does nmap show these 2 open ports?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by VanNostrand on 2007-09-22
Running nmap reveals this:

```
Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-21 22:05 PDT
Interesting ports on 192.168.0.2:
Not shown: 1695 closed ports
PORT    STATE SERVICE
111/tcp open  rpcbind
692/tcp open  unknown

```

My computer is behind a router and when I use a service like Shields UP it shows that my ports are stealthed.  Anyone have any idea why nmap shows these ports are open and should I be worried about them?

---

### Post by julian67 on 2007-09-22
Is your OS exactly as installed with no changes? Or are you sharing directories or printer across your network? Or applications which might use this functionality? These ports are open for client/server functions.

---

### Post by VanNostrand on 2007-09-22
Thanks for your reply.

I am not sharing any directories or printers on my network.  Unless I have done this by accident, I am unaware of any programs that would require these ports. 

I am assuming it would be safe to close both of these ports.  Searching through the forums I have learned how to close port 111 buy using the command: /etc/init.d/portmap stop, but I have yet to figure out how to close port 692.  Running netstat reveals:

```
sudo netstat -nle --program | grep 692
tcp        0      0 0.0.0.0:692             0.0.0.0:*               LISTEN     0          11408      4750/rpc.statd

```

---

### Post by julian67 on 2007-09-22
you need to scan from a different machine or your nmap results are probably meaningless.  You should scan again from a different machine and if the ports are seen as open then start researching what they do before deciding to close them. RPC is part of portmap. You need to find out what depends on portmap and see if you use it/need it and what else depends on it. I'm fairly confident that when you scan from a different machine you'll find there's nothing to worry about.

---

### Post by VanNostrand on 2007-09-22
I will scan from another computer as soon as I have access to one.  For now I start researching on the purpose of Portmap and RPC.

Thanks for your advice.

---

