---
title: "ath0 keeps receiving packet when idle"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-05-26
Hi,

    Just to make sure it is the norm. When I use the network connection to monitor my ath0 traffic, I realise that it keeps downloading (receiving packets) by about 10 packets a second (0.1mb in seconds?) even if I don't use any internet application.

     Is this normal? Why I ask is that I have been having slow internet whenever amule is used. Slow implies a substantial amount of timeout in firefox when amule is used. Setup in amule is by default so it is not that I have overshot the limits.

     I am also not too sure how to check if it is the ISP problem that they might have started restricting bandwidth limit.

      Any advice?

Thanks

---

### Post by hasimir44 on 2007-05-26
It's probably arp traffic (nodes asking where each other are..) or something else normal. 

If you're really curious, you could install ethereal and see what the packets are.. 

```
sudo apt-get install ethereal
```

you may need root access to monitor ath0 though. Once ethereal is installed, type this in a gui terminal to run it with root privs: 

```
gksu etheral
```

another awesome app for monitoring network traffic is etherape.

---

