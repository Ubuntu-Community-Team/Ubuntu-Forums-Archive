---
title: "service network"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by redr on 2007-05-23
I am new to ubuntu
I came to know about 'sudo /etc/init.d/networking' as a substitute for 'service network'
but unfortunately that isnt woking on my machine.
it gives the following message 
-bash: /etc/init.d/networking: No such file or directory
am i required to install something for this to work?

please help

---

### Post by Kobalt on 2007-05-23
What do you mean by "service network" ? What do you expect from this command line ?
You need to actually use it this way : ```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
sudo /etc/init.d/networking restart
```

---

### Post by redr on 2007-05-23
thanks 
i was trying for
 ```

sudo /etc/init.d/networking status

```
similar to
```

service network status 

```
in fedora

---

