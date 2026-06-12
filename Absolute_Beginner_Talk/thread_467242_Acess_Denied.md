---
title: "Acess Denied"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-07
if i write the following code and many others i am being denied acess despite being the only one to use the computer
```
network-admin
```

---

### Post by NeoLithium on 2007-06-07
Try using sudo ahead of the administrative tasks, it gievs you the proper root permissions to run them:
```

sudo network-admin

```

man sudo is a pretty good manual as well for some info on them :)

---

### Post by pardesi on 2007-06-07
thanks sir but is it precursor to some serious problems. i don't have my internet getting connected in ubuntu though it runs on windows.i have DHCP.any help will be gratly appreciated

---

### Post by NeoLithium on 2007-06-07
Hmmm, DHCP that rules out any password issues.  Are you just going from your modem to the computer or through a router?

Can you open up a terminal window (Applications -> Accessories -> Terminal) and copy and paste the output of this command:
```

cat /etc/network/interfaces

```

---

### Post by mlentink on 2007-06-07
It would be polite to point people to your other thread where you asked that DHCP question.

---

### Post by pardesi on 2007-06-07
no my modem is directly connected to the computer.is it of utmost necessity do that .because for that i have to go to ubuntu and then i can't reply to you.if is it necessary i will go.
should i use sudo before cat??

---

### Post by pardesi on 2007-06-07
> **mlentink said:**
> It would be polite to point people to your other thread where you asked that DHCP question.

yes sorry i was so frustrated that i just wanted thsi to be fixed .

---

### Post by NeoLithium on 2007-06-07
Not really, you might want to check through the Network stuff in System -> Administration -> Network.
Make sure your ethernet card is selected, and that your wired connection is made active.

---

### Post by pardesi on 2007-06-07
thanks i will do so then post.

---

### Post by pardesi on 2007-06-07
i got the following reply after 

```
cat /etc/network/interfaces
```
```
auto lo
iface loinet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

