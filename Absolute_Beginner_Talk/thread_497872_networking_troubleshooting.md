---
title: "networking troubleshooting"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by greyfox504 on 2007-07-10
I have a dell laptop b 130  with the intel pro wireless 2200b

I cannot connect to the internet thru my 2wire gateway.  I do not know how to configure it as in windows xp it did it sutomatically.

need help bad:) thank you

---

### Post by ukripper on 2007-07-11
First you have to make sure your wirless card is detected and configured in ubuntu.

Can you post output of the following command in terminal -

```
sudo lspci
```

```
sudo iwconfig
```

and also check in network manager if your wireless card is detected there.

and also paste output of following file -

```
sudo gedit /etc/network/interfaces
```

---

