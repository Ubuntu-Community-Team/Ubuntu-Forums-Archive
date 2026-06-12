---
title: "Program for WPA Access"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by mfmbcpman on 2006-11-24
My school uses WPA where you have to type in your school username and password. What program should I use? I am using the ipw3945.

---

### Post by deadgobby on 2006-11-24
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28WPA%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28WPA%29)

---

### Post by mfmbcpman on 2006-11-24
I get this error when I try the sudo apt-get. Where should Network Manager show up? Under Synaptic package manager, it says it is installed but i dont see it anywhere

```
michael@Michaellaptop:~$ sudo apt-get install network-manager-gnome
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
michael@Michaellaptop:~$ 

```

---

### Post by aysiu on 2006-11-24
You can't have Synaptic open while using *apt-get*.
Close Synaptic and try again.

---

### Post by PartisanEntity on 2006-11-24
As far as I understood it Network Manager only supports WEP, if you want to use WPA you will also (in addition to Network Manager) need wpasupplicant.

These instructions worked for me:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

