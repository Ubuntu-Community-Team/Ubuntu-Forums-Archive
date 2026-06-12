---
title: "Wireless PPPoE/VPN Connection Issues"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Schnoid on 2006-04-27
Hello,

I'm a complete Ubuntu n00b. Really enjoying using Ubuntu, but I have a big problem.

At my university, the only way to access the internet is through a VPN connection on a wireless network.

I've got the wireless card in my machine to connect to the access point, that's all OK, but, I'm struggling getting the PPPoE connection and the VPN connection to work.

I've ran "sudo pppoeconf" and it seemed to set everything up fine. It then said to type "pon dsl-provider" to start the connection. When I do this though, it returns plugin "rp-pppoe.so loaded" I don't think this is connected.

It may be trying to use the eth0 instead of ath0 but I'm really not sure.

Any help/suggestions greatly appreciated, as I cannot get the machine on the Internet any other way.

Thanks in advance.

Schnoid.

---

### Post by Woutie on 2006-04-28
I have the same problem with my university. Wireless network everywhere, but you need to connect with a VPN client to get to the internet.

I used vpnc and it works fine by me. The installation is not that hard. 
```
sudo apt-get install vpnc
```
to connect you need some information about the netword. the host, ID and netword password, your username and your password.

to start
```
sudo vpnc
```
Then he ask the information about your network.

It works great!!

---

