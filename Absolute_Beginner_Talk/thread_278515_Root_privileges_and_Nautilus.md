---
title: "Root privileges and Nautilus"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Ack99 on 2006-10-16
I need root privileges to create and move folders in my filesystem, ok, but i I start Nautilus in with sudo it enters in the Root's filesystem... ](*,) 

What is Firestarter adn how can I use it?

---

### Post by PriceChild on 2006-10-16
```
gksudo nautilus
```will open it up, go to /home/<<username>> to get to your dir.
You shuoldn't need root to do this though....
```
sudo chown <<username>>:<<username>> -R /home/<<username>>

```then use normal nautilus.

```
sudo aptitude install firestarter
```Installs the firestarter gui. It is a gui for iptables and allows you to edit the kernel's firewall.

---

