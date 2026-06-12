---
title: "vpn"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by lordsith on 2006-06-08
hello guys ! I'm a new ubuntu user and I need help configuring a vpn connection on ubuntu. can u please help me ? 10nx :confused:

---

### Post by sherlock-holmes on 2006-06-08
[QUOTE=lordsith]hello guys ! I'm a new ubuntu user and I need help configuring a vpn connection on ubuntu. can u please help me ? 10nx :confused:[/QUOTE]

try to use vpnc..

```
sudo apt-get install vpnc
```
then move to the vpnc folder 
```
cd /etc/vpnc
```
open the conf file
```
sudo gedit example.conf
```

edit as necessary...you will find the profile files from your school/office network. copy the  location and paste into the gateway, and the group passwd to the same etc...enter you username as the fourth entry (i think) which you use to login to the network..

connect vpnc,
```
sudo vpnc yournewprofile 
```
it will ask for password and then you will be good to go...

you can even add a plugin to the networkmanager...
```
sudo apt-get install network-manager-vpnc
```

hope this helps...

---

### Post by sigurdga on 2006-06-12
I could not find network-manager-vpnc. Does anybody know where it is hidden?

I searched using apt-cache (universe and multiverse enabled) and packages.ubuntu.com.

---

