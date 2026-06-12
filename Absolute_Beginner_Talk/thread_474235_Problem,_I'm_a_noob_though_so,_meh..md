---
title: "Problem, I'm a noob though so, meh."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Elias~ on 2007-06-14
Hi, I'm attempting to get my wireless internet going.  I've searched around and found out about Ndiswrapper.  I have a broadcom card.  When I install the bcmwl5.inf it works fine but bcmwl5.sys screwes up.  I'm on the newest Kubuntu release.  I would post over on Kubuntu forum but it is down right now so...  Here is my terminal stuff:


```
root@Cortana:~# ndiswrapper -i /home/elias/sp28537/bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
root@Cortana:~# ndiswrapper -i /home/elias/sp28537/bcmwl5.sys
installing bcmwl5.sys ...
couldn't get manufacturer section - installation may be incomplete
root@Cortana:~# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!
root@Cortana:~#     
```

---

### Post by Elias~ on 2007-06-14
Anyone know what is up?

---

### Post by lamalex on 2007-06-14
what broadcom card is it? have you tried the native driver? apt-get install bcm43xx-fwcutter

---

### Post by Elias~ on 2007-06-14
Wow, Thanks, that worked.  I'm sorry.  I am very new to all of this.  I'm liking Linux though!  Now I need some way to game on it.

---

### Post by Elias~ on 2007-06-14
Hm...  Little problem.  Now my connection fails every time I try to connect.  The wireless assistant sees my router and wireless internet but it fails when I try to connect.

---

