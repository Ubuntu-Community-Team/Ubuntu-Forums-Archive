---
title: "Point to point wifi connection (streaming)"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by popeye6984 on 2007-12-05
I've installed Ubuntu, set up (more or less) the video card, got wifi, installed gnump3d (media server) and now I'd like to do something like the following:
streaming music (stored in the ubuntu machine with gnump3d as server) with my Nokia N800 over wifi. I don't have a router ...how can I connect the two? Thanks

---

### Post by edm1 on 2007-12-05
click on the network-manager applet in the top right hand corner then create a new wireless network. pretty self explanatory from there on.

---

### Post by edm1 on 2007-12-05
alternatively to create an open unencrypted network type this in the terminal
```
sudo iwconfig eth1 essid NETWORK_NAME channel 11 key off mode ad-hoc
```

where eth1 is the wireless interface and NETWORK_NAME is what you want your network to be called.

---

### Post by popeye6984 on 2007-12-05
> **edm1 said:**
> click on the network-manager applet in the top right hand corner then create a new wireless network. pretty self explanatory from there on.

Sorry! I got xubuntu 6.06 and I can't found any "network-manager applet". But I got a network-admin in my system menu ... are they the same?

The network device is my wifi card which I suppose is the ath0 ... how to configure it with a minimum of security (I don't like to share all the music with the neighbours .... not yet) just put key "on" instead of "off"?

thank you

---

### Post by edm1 on 2007-12-05
i believe you just do "key 0123-4567-89"

have a look at the manual

```
man iwconfig
```

---

### Post by popeye6984 on 2007-12-05
OK I'll do that, thanks

---

### Post by popeye6984 on 2007-12-05
Sorry ... got another question: how should I "shut down" the connection from my computer? (I'm just making some experiments and I don't want the essid to work anymore)

---

### Post by edm1 on 2007-12-05
```
sudo ifconfig ath0 down
```

---

