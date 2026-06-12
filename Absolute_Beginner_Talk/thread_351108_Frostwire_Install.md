---
title: "Frostwire Install"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by oldstumpy on 2007-02-01
Hi:Folks ,i am haveing trouble with installing frostwire when i try to install here is what i get no matter what i dooldstumpy@oldstumpy-desktop:~$ /home/oldstumpy/frostwire-4.13.1.i586.deb_FILES/usr/lib/frostwire/runFrostwire.sh
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
oldstumpy@oldstumpy-desktop:~$ 

i have java verison installed in root/root/Desktop
/root/jre1.5.0_10
/root/jrel.5.0_10
I don't k,now what the problem is,:(  can anyone please help a old man that's a newbie:(

---

### Post by nixclusive on 2007-02-01
Hello there.. did you actually install java from the self extracting .bin file Sun provides?

---

### Post by nixclusive on 2007-02-01
from the output you've posted, i think making a symlink to your java installation in a place where Frostwire expects it should help. Open a terminal window and enter the following:```
sudo mkdir /opt
sudo ln -s /root/root/jrel.5.0_10 /opt/
```Try starting Frostwire after this.

---

### Post by oldstumpy on 2007-02-01
nixclusive thanks this is what i get when i do that

oldstumpy@oldstumpy-desktop:~$ sudo mkdir /opt
mkdir: cannot create directory `/opt': File exists
oldstumpy@oldstumpy-desktop:~$ sudo ln -s /root/root/jrel.5.0_10 /opt/

---

### Post by r4ik on 2007-02-01
sudo apt-get install sun-java5-jre sun-java5-plugin


wget -c [http://www.users.on.net/~stubby/FrostWire-4.10.9-2.i586.deb](http://www.users.on.net/~stubby/FrostWire-4.10.9-2.i586.deb)
sudo dpkg -i FrostWire-4.10.9-2.i586.deb

From,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Good luck !

---

### Post by Cariboo1938 on 2007-02-01
I installed Automatix from [HERE]("http://www.getautomatix.com/") and than
I choose -->File Share -->FrostWire to install. 
Automatix did it with installing all the necessities.
It worked for me without any error.

---

### Post by oldstumpy on 2007-02-02
Hi:All i wish to take time to say thak you very much to all who helped me get this done.
Thank's agian oldstumpy

---

