---
title: "synaptic died"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-04-03
My Synaptic has died.
I click on it and the whirly thing goes around, then nothing.

So...........what particular spell does one cast to fix this?

Phil

---

### Post by taurus on 2007-04-03
Either 

Applications -> Accessories -> Terminal
```
gksudo synaptic
```
or

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by raul_ on 2007-04-03
Also try 

```

sudo killall synaptic

```

and try opening it again

---

### Post by groeswenphil on 2007-04-03
I'm getting these sorts of messages.

sudo aptitude update
sudo: unable to lookup Ubuntu via gethostbyname()



$ sudo killall synaptic
sudo: unable to lookup Ubuntu via gethostbyname()

I fear we might need stronger spells?

Thanks,
Phil

---

### Post by taurus on 2007-04-03
Okay, did you change the name of your computer or something similar to that?  What are the output of these two commands from a terminal?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by groeswenphil on 2007-04-04
Yes.......I did change the name whilst trying to get my Network working.
It is working now.

Output from the last two commands was 

~$ cat /etc/hosts
127.0.0.1 localhost Ubuntu
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

