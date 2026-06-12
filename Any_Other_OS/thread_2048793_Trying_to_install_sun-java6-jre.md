---
title: "Trying to install sun-java6-jre"
date: 2012-08-27
forum: Any Other OS
---

### Post by ludo1960 on 2012-08-27
Hello,

On my debian box I am trying to install sun-java6-jre

I added contrib non-free to my sorces list ran update then:

apt-get install package sun-java6-jre
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package package

I tried this s few days ago on another machine and it worked, so not sure what is going on here. Anyone got any ideas?

Thanks..

---

### Post by Cheesemill on 2012-08-27
For legal reason Oracle Java is no longer available in any of the standard repositories. Also you are better of using Java 7, version 6 has been depreciated and has known security issues.
The easiest way to install is to do:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

```

Oops, just noticed you are using Debian.
Debian instructions are:
```
su -
echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main" > /etc/apt/sources.list.d/webupd8team-java.list
echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main" >> /etc/apt/sources.list.d/webupd8team-java.list
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
apt-get update
apt-get install oracle-java7-installer
exit
```

---

### Post by ludo1960 on 2012-08-27
Worked like a charm first time! You're a star, thank you very much indeed  ):P

---

### Post by raja.genupula on 2012-08-27
Thats glad news , now please mark your thread as solved from thread tools . Thank you .

---

### Post by oldos2er on 2012-08-27
Moved to Other OS/Distro Talk.

---

