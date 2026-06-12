---
title: "spikes in network while idle..."
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-21
when i go to the system monior, i notice that in my network history theres a spike of activity about every 10 seconds or so even though im not using the internet at all. is this normal? its flat idle but then there are spikes....i get a lot of "recieved" than i do "sent" i dont know if this happened when i had XP...

---

### Post by wormser on 2008-04-21
There are a lot of programs for monitoring your network.  Try iftop.  Applications> Accessories> Terminal.

```
sudo apt-get install iftop
```To run it
```
sudo iftop
```Ntop is another popular one with a web interface.

```
 sudo apt-get install ntop -y
``````
sudo ntop --set-admin-password
``````
sudo ntop -u ntop -d
```Now open up Firefox and go to [http://localhost:3000/](http://localhost:3000/).

---

