---
title: "ifconfig"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by shredfitz on 2007-11-19
I need to be able to execute linux network utilities like ifconfig while logged in as a user on my school's server. when I am logged in I type ifconfig and it says 'command' not found. I then figured that I have to use an export PATH command, but I am stuck trying to determine what directory this path should be to.

I have something like this:

export PATH=$PATH:/and/the/path/goes/here/but/i/cannot/figure/out/what/path/I should/be/using

And then I am assuming I can use the ifconfig command and get what I am looking for? 

i have tried /etc/sysconfig/network-scripts/ifcfg-eth0 

i have tried /etc/rc.d/init.d/network

i have tried /dev/eth0

These are all mentioned in my text book and I cant get any of them to work.

---

### Post by nick_h on 2007-11-19
You probably need the following in your path - 

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

ifconfig is in /sbin

---

### Post by llamakc on 2007-11-19
More likely the location is not in YOUR path, so you need to use the full path to ifconfig.

See if you can find it with:

```

which ifconfig

```

---

### Post by shredfitz on 2007-11-19
thanks to you both. I figured it out (with your help).

---

