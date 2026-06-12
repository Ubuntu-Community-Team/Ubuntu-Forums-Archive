---
title: "Ndis wrapper install help"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by nphoops on 2007-03-07
I really love Ubuntu, but I won't be able to do a lot if I can't go online, so I tried to install Ndis Wrapper so I could use my D-Link wireless USB device. the "make uninstall" command works, but when I try the "make" and "make install" it says that there are errors.  :confused:  I really need some help!

btw, I'm using the Ubuntu version that is downloaded via Wubi.

---

### Post by endtroducing on 2007-03-07
What is Wubi? What errors do you get?

Did you read this: [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

E

---

### Post by nphoops on 2007-03-07
wubi lets you install UBUNTU via Windows

---

### Post by nphoops on 2007-03-07
that link you gave me didnt help

---

### Post by nadarockyraccoon on 2007-03-07
so what you need to to do is open your repositories so that that you can download the debian package instead of trying to use a tar package. This is done by opening a terminal and typing "sudo gedit /etc/apt/sources.list" and uncommenting the deb and deb-src lines. then save that and and close it and type in the terminal "sudo apt-get update" now open you synaptics package manager and search ndiswrapper. I would go with version 1.8 but the older version may work better. To be honest I've never had much luck with ndiswrapper and i would research that card to see if it is supported by prism or madwifi.

---

