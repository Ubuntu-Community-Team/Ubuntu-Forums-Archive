---
title: "Extra Repository Help Please"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by SOG420 on 2006-03-09
OK I have read the Unofficial Guide and in order to add extra repositories I need to find "## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted"......
I'm Not seeing this?
 I am seeing "deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository."......
 Total Linux N00b please help

---

### Post by Lord Illidan on 2006-03-09
In order to add extra repositories, remove the # in front of any line which starts like this :  deb [http://]("http://us.archive.ubuntu.com/ubuntu")
or deb-src

Lines which are normal English - leave them alone, they are supposed to be commented.
[]("http://us.archive.ubuntu.com/ubuntu")

---

### Post by SOG420 on 2006-03-09
OK DID that Then tried to Install Java and got this"
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
"
So I did what it asked then did this "wm@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Thanks so much for the help :)

---

### Post by aysiu on 2006-03-09
Try this:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

---

### Post by Lord Illidan on 2006-03-09
[quote=SOG420]OK DID that Then tried to Install Java and got this"
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com]("http://security.ubuntu.com") hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
"
So I did what it asked then did this "wm@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Thanks so much for the help :)[/quote]

My bad... I forgot to tell you to run ```
sudo apt-get update
```

---

### Post by mstlyevil on 2006-03-09
If none of that works try adding this line to your sources list.

```
sudo gedit /etc/apt/sources.list
```

Add this line at the end

```
deb http://ubuntu.tower-net.de/ubuntu/ breezy java
```

Save the file and then run

```
sudo apt-get update
```

You should be able to install java after that.

---

