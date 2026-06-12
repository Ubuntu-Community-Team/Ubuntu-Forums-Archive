---
title: "slow internet connection"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-01-29
Dear friends, I am experiencing a very slow internet connection in Ubuntu. Pages take much time to open, download is sluggish!
I have disabled IPv6 in network.dns. But it didn't work. Kindly help.
Thanks and regards,
Saurav

---

### Post by RomeReactor on 2007-01-29
Open a terminal and type:

```
sudo gedit /etc/modprobe.d/aliases
```

to disable ipv6 globally, then reboot.

---

### Post by abu-fatu on 2007-01-29
i got this from another thread in this forum: change the dns numbers to this:208.67.222.222
208.67.220.220 as your primirary and secondary dns numbers. it really improved my internet connection.

---

### Post by RomeReactor on 2007-01-29
Good to hear it worked for you! :mrgreen:

---

### Post by RomeReactor on 2007-01-31
Didn't notice that my first post got chopped, so here goes again: On a terminal type:

```
sudo gedit /etc/modprobe.d/aliases
```

then look for

```
alias net-pf-10 ipv6
```

and change it to

```
alias net-pf-10 off
```

Save and reboot.

---

