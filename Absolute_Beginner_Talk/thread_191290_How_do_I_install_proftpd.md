---
title: "How do I install proftpd"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Russellh on 2006-06-07
Please help I am very very new to Linux.

I am trying to install proftpd
I run command sudo apt-get install proftpd

and get message

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd


I have been to proftpd website and down loaded .rpm file, is this correct file i download to desktop, is this correct place.

Can someone give me an idiot guide to install package, i have looked at forums but no luck.

Thanks 


Russell.

---

### Post by carlosqueso on 2006-06-07
Allright, first you neet to add the Universe repository to your sources.list.   First open a terminal and type ```
sudo gedit /etc/apt/sources.list
```  Then you need to replace what is there with ```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

Then you should run the sudo apt-get install proftpd and it should work.

---

### Post by uzi09 on 2006-06-07
oh here it is!
i saw this thread earlier, wrote a nice lil reply and everything and when i went to submit, it said "ubuntu forums are now offline" :( lost everything :S

basically if the above doesn't work, download a program called alien
```

sudo aptitude install alien

```
then convert the .rpm file (used by Red Hat mainly) to .deb by running this command:
```

alien file.rpm

```
now install the .deb file with this:
```

sudo dpkg -i file.deb

```

---

