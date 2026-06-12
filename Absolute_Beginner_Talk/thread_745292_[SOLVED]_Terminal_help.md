---
title: "[SOLVED] Terminal help"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Totz on 2008-04-04
Hey all, Im completely new to Ubuntu, this is such a n00bish question probably but here it goes.

When I run the terminal and enter a command it asks me for a password, however I never set up a password for it + it wont actually let me type one in when prompted :/ Any advice? Thanks

---

### Post by oldos2er on 2008-04-04
Use the same password you use to login. Just type it in; it will not echo on the screen; and press Enter when done.

---

### Post by Oldsoldier2003 on 2008-04-04
> **Totz said:**
> Hey all, Im completely new to Ubuntu, this is such a n00bish question probably but here it goes.

When I run the terminal and enter a command it asks me for a password, however I never set up a password for it + it wont actually let me type one in when prompted :/ Any advice? Thanks

whenever you run a command  using sudo the terminal will ask you for your user password in order to escalate you to superuser status. the password is not shown as you type it, its a security feature.

---

### Post by Totz on 2008-04-04
Thanks guys, I litterally have no idea about this OS, just installed it today. Already prefer it to Vista though :D

Also, is there a command to Ping and Tracert for terminal?

---

### Post by Cannaregio on 2008-04-04
> **Totz said:**
> Also, is there a command to Ping and Tracert for terminal?

ping and traceroute, but  install [mtr]("http://www.bitwizard.nl/mtr/") (my trace route), a allinone traceroute+ping that substitutes traceroute and beats it black and blue.

```
sudo apt-get install mtr
```

Invoke mtr

```
sudo mtr google.com
```

And use the "n" key to switch between DNS-names and IPs.

---

### Post by Oldsoldier2003 on 2008-04-04
> **Totz said:**
> Thanks guys, I litterally have no idea about this OS, just installed it today. Already prefer it to Vista though :D

Also, is there a command to Ping and Tracert for terminal?
```

ping -c 5 <someaddress>
``` will send 5 pings
```
sudo tracert <someaddress>
``` will run tracert

for more complete info
```
man tracert
man ping
```

---

### Post by Totz on 2008-04-04
> **Cannaregio said:**
> ping and traceroute, but  install [mtr]("http://www.bitwizard.nl/mtr/") (my trace route), a allinone traceroute+ping that substitutes traceroute and beats it black and blue.

Use the "n" key to switch between DNS-names and IPs.

Excellent, thank you so much :)

---

### Post by Dr Small on 2008-04-04
Oldsoldier2003, "tracert" is a DOS command. The proper command it:
```
traceroute
```

Cheers!
Dr Small

---

### Post by Cannaregio on 2008-04-04
> **Totz said:**
> Excellent, thank you so much :)

Enjoy.
Maybe you should change your thread to "SOLVED".

---

### Post by Oldsoldier2003 on 2008-04-04
> **Dr Small said:**
> Oldsoldier2003, "tracert" is a DOS command. The proper command it:
```
traceroute
```

Cheers!
Dr Small

type tracert in a terminal. it works in linux as well :)
```
chuck@chuck-desktop:~$ which tracert
/usr/bin/tracert
```
looks like linux to me

---

