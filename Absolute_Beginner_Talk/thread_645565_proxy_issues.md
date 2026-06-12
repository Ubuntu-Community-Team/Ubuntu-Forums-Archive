---
title: "proxy issues"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by crazysexycool on 2007-12-20
I am getting the following error when i try to get something of the synaptic package manager

i am using the internet on this laptop behind a proxy any ideas my apt.conf file is modified all passwords changed back to the new one what am i doing wrong

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.3.0.0debian1-4build1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.3.0.0debian1-4build1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-6_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-6_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]

---

### Post by lord_zerg on 2007-12-20
it seemms you need to configure synaptic to go through the proxy. you can do that from the gui
configure -> preferences -> network
there choose manual configuration and enter your proxy data. example
proxy.blahblah.com port 9090

hope that helps

---

### Post by crazysexycool on 2007-12-20
hi i have set that up already still getting same error

---

### Post by lord_zerg on 2007-12-20
when setting that up, did you enter the username and password for your proxy?

---

### Post by crazysexycool on 2007-12-20
yes i have set it up with username and password do you know how the apt.conf file is supposed to look so i can compare it to mine though i doubt thats  the problem

---

