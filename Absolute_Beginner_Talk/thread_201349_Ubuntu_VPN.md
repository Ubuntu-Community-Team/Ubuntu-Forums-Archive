---
title: "Ubuntu VPN?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by swaldroup on 2006-06-21
I am just now downloading Unbuntu and my main goal is to set up a VPN. I know this is getting a little deep for a linux beginner, but is this something that can be done with ubuntu?  If so what kind of VPN software recomendations mith there be?
Thanksfor any help!

---

### Post by jvl on 2006-06-21
OpenVPN is relatively easy to set up. 

[http://openvpn.net/howto.html](http://openvpn.net/howto.html)

There is package as well.

---

### Post by neoflight on 2006-06-22
[QUOTE=swaldroup]I am just now downloading Unbuntu and my main goal is to set up a VPN. I know this is getting a little deep for a linux beginner, but is this something that can be done with ubuntu?  If so what kind of VPN software recomendations mith there be?
Thanksfor any help![/QUOTE]


you can use vpnc too...(you dont need linux-headers for this...for ciscovpn you do.)

```
sudo apt-get install vpnc
```

its very easy to set up....in 5 min....

you will have a config file in /etc/vpnc/ called example.conf and you can edit that file to get your networking set -up...copy certain data from cisco-vpn profile file you are interested in.

you can have a network-manager-plugin for vpnc too...

```
sudo apt-get install network-manager-vpnc
```

[http://www.ubuntuforums.org/showthread.php?t=16434&highlight=vpnc](http://www.ubuntuforums.org/showthread.php?t=16434&highlight=vpnc)
[http://www.ubuntuforums.org/showthread.php?t=95334](http://www.ubuntuforums.org/showthread.php?t=95334)

---

### Post by danpre on 2006-06-22
Do you want to start VPN server or just need VPN client?

For clients you can take a look in [KVPNC]("http://home.gna.org/kvpnc/en/index.html")  if you are using KDE.

I'm using original CISCO VPN CLIENT (command line only) and it works fine for me.

danpre

---

### Post by swaldroup on 2006-06-22
yes i will be setting up a VPN server.  I have mostly WIndow machines on my network, but I don't want to dish out more money to mr gates and company for another OS.  Besides I need to learn more about Linux and this gives the a good reason and opporunity.

Thanks

---

