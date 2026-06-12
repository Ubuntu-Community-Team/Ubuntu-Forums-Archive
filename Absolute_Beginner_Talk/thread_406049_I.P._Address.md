---
title: "I.P. Address"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-04-10
I am trying to make a windows XP PC find my Ubuntu PC on a home network.
How can I find the IP Address of my Ubuntu PC?

---

### Post by annda on 2007-04-10
if you have the network manager applet right click on it and select connection information.

otherwise, type in the terminal
ifconfig

---

### Post by apjone on 2007-04-10
open a terminal and type 
```

ifconfig

```
or
System > Administration > Networking 
and it will be listed as Address: xxx.xxx.xxx.xxx

---

### Post by steve.horsley on 2007-04-10
Open a command prompt (Accessories->Terminal) and enter the command **ifconfig** . Look for the line starting "inet addr:" but it's not the 127.0.0.1 line.

---

