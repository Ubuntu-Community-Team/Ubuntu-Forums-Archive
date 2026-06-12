---
title: "nmcli: command not found, ubuntu 10.04 ppc"
date: 2012-09-26
forum: Apple Hardware Users
---

### Post by theDole on 2012-09-26
Moving on with the mac-project I am trying to get a script running that uses nmcli to manipulate network connections. It works great on my pc with 10.10 however on the powerbook I get for example:
```
$ nmcli -p con status
nmcli: command not found
```Is there any reason that the network manager wouldn't have these functionalities in 10.04 ppc? I am currently writing this on the powerbook so networking works fine i general.
I should probably also add that I am trying to learn this stuff by doing it, so If I made some basic errors don't be too harsh.

---

### Post by theDole on 2012-09-28
So, for anyone finding this later:
It seems nmcli (which is a command line user interface for networking) is installed in 10.10 versions and later. I have been unable to install it on my 10.04 installation as well, which I find rather weird but whatever. I am solving the problem by going for Lubuntu 12.04 instead.

---

