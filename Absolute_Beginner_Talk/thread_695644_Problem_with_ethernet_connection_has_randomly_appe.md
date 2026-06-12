---
title: "Problem with ethernet connection has randomly appeared"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by spaceknight019283 on 2008-02-13
Yesterday I installed Ubuntu and everything was working great and I loved it. But today for some reason I cannot connect to the internet at all. I can connect on my windows partition though which leads me to believe that it is linux. When I type in 'dhclient' it renews the stuff like it should, so I am really confused. And when I ping [www.google.com](www.google.com) I get a timeout. And theworst part is that the networking connection shown in the upper right hand connection says I am connected. Is there any easy way to fix this?

p.s. The only 2 questionable applications I have installed are Envy and MoBlock. I think MoBlock is the source of my problems, so I am looking up how to shut it off right now and I will post later. I dont think it is the reason because I did not tell it to start at boot up.

---

### Post by Cypher on 2008-02-13
MoBlock could certainly be cause some issues..while Ubuntu claims to be connected, type the following in the console
```

/sbin/ifconfig

```
This will show what IP address you have..

Additionally, if you are connecting to the Internet through a router (and you really should be if not) then you don't really need to run a software firewall on your PC as well..

---

### Post by spaceknight019283 on 2008-02-13
Yeah it turns out its MoBlock. To stop this problem you have to type "sudo moblock-control stop". This is pretty f'd up imho, because after reading the documentation for it ([https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)) I realized that it does automatically start upon booting and edited the /etc/moblock/moblock.conf and changed the MOBLOCK_INIT to 0.

---

### Post by jan quark on 2008-02-13
please mark this thread as solved when it is solved for you

thank you

---

