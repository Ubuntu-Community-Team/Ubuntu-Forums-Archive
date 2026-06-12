---
title: "Black screen after ubuntu loads (Powerpc)"
date: 2010-08-31
forum: Apple Hardware Users
---

### Post by Tenrai on 2010-08-31
Hey, finally just got ubuntu to install on my emac a1002, I had to use the powerpc version. The install went fine, it restarted and loaded ubuntu, but after it loads goes to a blank black screen. And I imagine it sits there forever, yet I've only left if for about 5mins or so.

The emac is from 2003, and has a 1ghz processor (Powerpc) and has 256mb ram.

So is there any solution to this, please help. I am new to both Linux and Mac.

---

### Post by linuxopjemac on 2010-09-01
boot in single user mode (Linux 1)

then you have to download an existing xorg.conf file and move it to the right place:
```

wget http://mac.linux.be/files/xorg/emac2.txt
sudo mv emac2.txt /etc/X11/xorg.conf
```

Tell us if it works. If not, give me the output of:

```
sudo cat /var/log/Xorg.0.log
```

---

