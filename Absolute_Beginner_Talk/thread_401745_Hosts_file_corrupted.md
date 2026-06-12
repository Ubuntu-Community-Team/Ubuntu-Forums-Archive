---
title: "Hosts file corrupted"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by subhamay on 2007-04-04
While trying to setup Zimbra, I have edied and saved my  /etc/hosts file with " Action > Edit As Root" option in Konqueror. But my entries are wrong. My problem is I cannot re-edit the same file with same option and the 
```
Su returned with an error
``` 
message is coming. Pls help me.

---

### Post by cypherzero on 2007-04-04
have you tried just using the terminal?
sudo nano <filename>

---

### Post by subhamay on 2007-04-05
I followed your advice and issued follwing command:
```
sudo nano hosts
```
and got the following message
```
sudo: unable to lookup <mymachinename> via gethostbyname()
```

---

