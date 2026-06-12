---
title: "Can't use make and make install."
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Nordoelum on 2006-04-21
Greetings,

I am using XFCE for my server. But now I have started to compile my software by my self. Since the one hosted by the repos is outdated.

Am trying to compile Apache2.2.0, but after I have using the ./configure command, I can't use the make command:
```
bash: make: command not found
```

How to solve this?

---

### Post by unbuntu on 2006-04-21
[QUOTE=Nordoelum]Greetings,

I am using XFCE for my server. But now I have started to compile my software by my self. Since the one hosted by the repos is outdated.

Am trying to compile Apache2.2.0, but after I have using the ./configure command, I can't use the make command:
```
bash: make: command not found
```

How to solve this?[/QUOTE]

Do this first:
```

sudo apt-get install make

```

---

### Post by Nordoelum on 2006-04-21
Solved! Just did a:
```
$ sudo aptitude install make
```

---

### Post by Nordoelum on 2006-04-21
[quote=unbuntu]Do this first:
```

sudo apt-get install make

```[/quote]
Thanks for the help, much appreciated :D

---

### Post by patrick295767 on 2006-04-21
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 
apt-get -f -y install amsn 

### chat stuffs like amsn
apt-get -f -y install kadu gaim
apt-get -f -y install gaim  kopete
apt-get -f -y install 


## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
apt-get -f -y install
apt-get -f -y install

---

