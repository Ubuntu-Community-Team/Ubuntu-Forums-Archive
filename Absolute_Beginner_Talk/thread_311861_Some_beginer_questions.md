---
title: "Some beginer questions"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Breeman on 2006-12-03
Hi,

I recently installed Ubuntu 6.10 "Edgy Eft" on my computer. When I went to change my repository settings to install Firefox 2.0 all the repository names where for Dapper Drake, and I was wondering if this was normal or if I had downloaded the wrong .ISO. Is there any command to tell which version I have installed?

Also is there a way that I can display my computers temp and current voltage? I have an ASUS motherboard, and in windows I used their PC Probe utility to monitior the current levels. Unfocently ASUS does not provide a Linux install, and I would like to still be able to see that information.

Finaly, I'm thinking about getting a MacBook, is there any know compattibly prolbems with dual booting Linux and OSX on the MacBook?

Thanks in advance,
Breeman

---

### Post by johnnymac on 2006-12-03
Sounds like you installed Dapper instead (6.06LTS) - which is the current Long-Term-Support distro.  If you want though...you can change that into Edgy by doing the following:

1.  Open sources.list and change all dapper to edgy - save the file
```

sudo gedit /etc/apt/sources.list

```

2.  Issue the following commands from a terminal
```

sudo apt-get update
sudo apt-get dist-upgrade

```

This will take a while.

The other option is to download this file (which is Edgy)

[http://ubuntu.cs.utah.edu/releases/edgy/ubuntu-6.10-desktop-i386.iso](http://ubuntu.cs.utah.edu/releases/edgy/ubuntu-6.10-desktop-i386.iso)

---

### Post by taurus on 2006-12-03
1.  Edgy comes with firefox 2.0 while Dapper is using version 1.5!!!  So, do you plan to use firefox 1.5???

2.  You need to install lm-sensor and configure it...

3.  Don't know any about MacBook and don't really care!  ;)

---

