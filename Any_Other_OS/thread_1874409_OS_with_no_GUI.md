---
title: "OS with no GUI?"
date: 2011-11-03
forum: Any Other OS
---

### Post by marenkar on 2011-11-03
Hey guys!

I was looking for an OS with no GUI and just text. I somewhat co-managed a server using Red Hat over the summer and I'd like to practice more with a pure text Operating System. I tried just using Terminal on Ubuntu, but I want to be forced to just use text commands to do what I want to. 

Any ideas? Similar commands with Red Hat (so basically Unix) would be great.

---

### Post by lisati on 2011-11-03
Ubuntu server edition comes without a GUI.

---

### Post by marenkar on 2011-11-03
Hmm can the Ubuntu server edition run on a laptop just fine?

---

### Post by wojox on 2011-11-03
Also minimal Fedora, CentOS and Scientific Linux are good Red Hat alternatives.

---

### Post by marenkar on 2011-11-03
> **wojox said:**
> Also minimal Fedora, CentOS and Scientific Linux are good Red Hat alternatives.

Minimal Fedora looks great! I'll take that. Thanks!!

---

### Post by wolfen69 on 2011-11-03
> **marenkar said:**
> Hmm can the Ubuntu server edition run on a laptop just fine?

On a laptop, I would just do a minimal install of regular ubuntu.

---

### Post by markbl on 2011-11-03
Given you are posting on the ubuntu forums then ubuntu server would be the best solution. Or use the debian net installer for something very small and minimal. Use gnu screen to give you multiple parallel terminal sessions.

---

### Post by gardnan on 2011-11-03
> **marenkar said:**
> Minimal Fedora looks great! I'll take that. Thanks!!
What is this "Minimal Fedora" and where can I find it? Is it a custom spin?

---

### Post by v1ad on 2011-11-03
with fedora if i remember correctly, you download the normal copy and just do a minimal install. i recommend just a regular server distro, like ubuntu server. If you really want to mess around download backtrack and don't do startx, this will give you the console with a lot of fun hacking tools and at the same time it give you the gui, just in case you will need it.

---

### Post by TeamRocket1233c on 2011-11-03
FreeBSD minimal install (if possible), OpenBSD (as it usually makes you build your OS from the ground-up once it's installed), minimal install of ANY currently active Linux distro, or FreeDOS.

---

### Post by wojox on 2011-11-03
> **gardnan said:**
> What is this "Minimal Fedora" and where can I find it? Is it a custom spin?

[http://ftp.jaist.ac.jp/pub/Linux/Fedora/releases/15/Fedora/x86_64/]("http://ftp.jaist.ac.jp/pub/Linux/Fedora/releases/15/Fedora/x86_64/")

---

### Post by shobon on 2011-11-03
Arch is bit of an obvious answer. Fedora has a weird naming scheme for network devices now.

---

### Post by Glenn nl on 2011-11-04
Ubuntu Minimal + Elinks + Mutt + Cmus + Midnight Commander. :)

Install the Ubuntu Minimal: 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

When finished type:

```
sudo apt-get update && sudo apt-get upgrade
```

followed by:

```
sudo apt-get install elinks mutt cmus mc
```

This will install a simple CLI browser, mail-program, music player and file manager.

Good luck. :popcorn:

---

### Post by memilanuk on 2011-11-04
I can't believe no one has put this forth yet...

plain ole vanilla Debian ;)

---

### Post by SkyNet2029 on 2011-11-04
A vanilla install of Debian would get you just what you are looking for, without the added overhead of applications you would have no use of. A netinstall cd or even just the Install CD-1 would also be a great starting point.

---

### Post by dniMretsaM on 2011-11-04
I would have to recommend [Linux From Scratch]("http://www.linuxfromscratch.org/"). Building one myself.

---

