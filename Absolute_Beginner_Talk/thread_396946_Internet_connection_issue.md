---
title: "Internet connection issue"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by mrabalaji on 2007-03-30
Hi,
       I tried to configure the internet connection to ubuntu 7.04 beta but it was not possible my internet provider has given me a static ip and i have configured in the <Network> tab,now i can ping to my gateway(10.163.33.1)  but when i'm trying to connect to internet it is not connectinig. Ususally in windows  there would be webpage which will authenticate my connection to my ISP but that page it is not shown in Ubuntu for firefox browser.when i have checked the conneciton details i'm unable to find the primary dns and secondary dns address ,

                  but i have entered the info  in the network configuration part under <DNS> tab,but they are not reflected in the connection information,so is this a problem for my internet connection,

       pls clarify

---

### Post by zvacet on 2007-03-30
> disabling network manager in the sessions/startup bit, and typing 

sudo ifup eth0
sudo ifdown eth0
sudo ifup etho

That is what I found.hope it help.

---

