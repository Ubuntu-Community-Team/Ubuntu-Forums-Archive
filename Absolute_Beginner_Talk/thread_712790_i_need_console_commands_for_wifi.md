---
title: "i need console commands for wifi"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by cpu_medic on 2008-03-02
i need console commands for connecting to a wep protected network.(its mine dont worry) i need to download envy so my vid card will work, and no i cant hardwire. am i burnt?:confused:

---

### Post by jan quark on 2008-03-02
> i need console commands for connecting to a wep protected network.

you want to set up a wlan connection right?
 please post the output from these terminal commands first:

```
iwconfig
```

```
sudo iwlist scan
```

```
sudo lshw -C network
```
```

cat /etc/network/interfaces
```

they won't enable your wlan but will help to clarify your network status so we know little more to help you

---

### Post by cpu_medic on 2008-03-02
wow so i installed a netgear wg311 lastnite and installed ubuntu 7.10 tonite, and i dont think ubuntu sees it. 

lo: no wireless extention

eth0: no wireless extention


i have already downloaded envy on my other machine. can i burn it to a cd and install it in code from the cd?

---

### Post by GooblyWoobly on 2008-03-02
Assuming you got the .deb file for envy, you can install it from CD/USB stick by doing :
```
dpkg -i <envy .deb file>
```

---

### Post by cpu_medic on 2008-03-02
"cannot access arcive: no such file or directory

---

