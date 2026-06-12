---
title: "Oh my God that scared me."
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2007-01-21
I was logging into Xubuntu and it tells me, right after I log in but before I can use any app or see any panels, that I need to do something with my "host" file in /etc/hosts ... Uh... It told me the internet wouldn't work, but it's working, so - what the hell just happened? Is it going to do this every time I log in now?

---

### Post by taurus on 2007-01-21
Did you play around with your network config files?  What do these files look like?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by SZF2001 on 2007-01-21
For the second one you told me to use, I got this:

```

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by taurus on 2007-01-21
That's all you have for /etc/hosts!  And there is nothing in /etc/hostname.  You have done a major job to your machine.  See if this command work at all.

```
sudo apt-get update
```

---

### Post by Shatrat on 2007-01-21
What about hostname?

In the /etc/hosts there should be a couple entries above what you posted.
There should be a 127.0.0.1  localhost and a 127.0.1.1 hostname (where hostname matches what is in /etc/hostname)

---

