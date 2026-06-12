---
title: "Apache Install"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by maxding on 2007-02-23
I installed apache2 from the synaptic but cannot find it now that i have installed it.  I tried first to install through the shell but realized that i could just just use the synaptic.  Help would be greatly appreciated.  Thankyou,

Max

---

### Post by chggr on 2007-02-23
If you want to start Apache, type in the following command:
sudo /etc/init.d/apache2 start
If you want to stop it, use "stop" instead of "start".

The configuration file for apache is /etc/apache2/apache2.conf

---

### Post by maxding on 2007-02-23
oh thankyou.

---

### Post by kebbelj on 2007-02-23
I finished writing over Fedora with Ubuntu CE about 30 minutes ago and began poking around my new distro. I need a web server because I do PHP and MySQL development. Firefox with 127.0.0.1 didn't show me anything. Typing httpd -v didn't get me any info either. I searched the forum and wound up here. I tried *sudo /etc/init.d/apache2 start* and got nothing. When I looked there's no Apache in either /etc or /etc/init.d.

I've been using Yellowdog and Fedora Linux for years as a hobby. I'm not a novice, but I'm certainly no Linux expert. Earlier this evening, I would have used yum to install Apache. Now that I'm a Ubuntu kind of guy, how should I approach the install?

---

### Post by maxding on 2007-02-23
i just learned this one myself.

applications--> add/remove ---> advanced then scroll down and mark apache2 for install along with the mods you want.

---

### Post by spoot on 2007-02-23
> **kebbelj said:**
> Earlier this evening, I would have used yum to install Apache. Now that I'm a Ubuntu kind of guy, how should I approach the install?
If you're used to yum, apt-get or aptitude are probably the programs you are after ;) Example:

```
apt-get install apache2
```

OR

```
aptitude install apache2
```

(not sure if this is the correct package name, just an example)

---

### Post by irish_flu on 2007-02-24
With Ubuntu (assuming you're running gnome here), you also use "Synaptic Package Manager".

System--> Administration--> Synaptic Package Manager

search for "apache" and anything else you want, like "mod-python", etc.  As you find each one, mark it for install and then hit "apply".

Synaptic provides you with more options and freedom than "Add/Remove", yet is more friendly (IMHO) than apt-get or aptitude.  Not trying to tell you how you should do it, just providing you with options.  :)

---

### Post by balbir97 on 2007-02-27
> apt-get install apahce2

or

```
aptitude install apache2
```

---

