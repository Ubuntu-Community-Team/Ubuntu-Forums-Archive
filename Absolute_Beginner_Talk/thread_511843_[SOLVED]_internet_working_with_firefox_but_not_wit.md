---
title: "[SOLVED] internet working with firefox but not with lynx"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by daydan on 2007-07-28
hello,
this appeared those days. i dont really know why but. Internet is working in some programs but not in all. Firefox, Gftp, Telnet (terminal), Netcat, they all work . But Lynx, Synaptic doesnt. Even if i try lynx 127.0.0.1 it is not working, though it read be opened in firefox. I could make updates with synaptic before, but i dont know why some programs are unable to connect to the internet.
What to do?
thank you
daniel

---

### Post by Pragmatist on 2007-07-28
What happens if you type this in a terminal:
```
sudo apt-get update
```

---

### Post by daydan on 2007-07-28
daniel@standbox86:~$ sudo apt-get update
Password:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty Release.gpg
  Connexion à localhost: 4001 (127.0.0.1) impossible. - connect (111 Connexion refusée)
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/main Translation-fr
  Connexion à localhost: 4001 (127.0.0.1) impossible. - connect (111 Connexion refusée)
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/restricted Translation-fr
  Connexion à localhost: 4001 (127.0.0.1) impossible. - connect (111 Connexion refusée)
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/universe Translation-fr
  Connexion à localhost: 4001 (127.0.0.1) impossible. - connect (111 Connexion refusée)

i goes on like that with the same error.


Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-fr
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-fr
Impossible de récupérer [http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Connexion à localhost: 4001 (127.0.0.1) impossible. - connect (111 Connexion refusée)

---

### Post by Pragmatist on 2007-07-28
Please post your: **/etc/apt/sources.list**

---

### Post by daydan on 2007-07-28
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-security multiverse



I seems the problem doesnt come from here...

---

### Post by Pragmatist on 2007-07-28
The message you get complains about GPG.  See if this helps:
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077](https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077)

---

### Post by daydan on 2007-07-28
But why lynx is unable to connect? there is no link with synaptic.

---

### Post by daydan on 2007-07-28
ok :
here is something interesting/

daniel@standbox86:~$ lynx [www.hotmail.com](www.hotmail.com) > a.txt
daniel@standbox86:~$ cat a.txt

Recherche [www.hotmail.com](www.hotmail.com) premier
Recherche localhost:4001
Connexion HTTP à localhost:4001
Alerte! : Impossible d'établir une connexion à l'hôte distant

lynx : accès impossible au fichier de départ [http://www.hotmail.com/](http://www.hotmail.com/)


---
Lynx is connecting from localhost on port 4001. ?????????? does someone know how to change this?

---

### Post by Pragmatist on 2007-07-28
> **daydan said:**
> But why lynx is unable to connect? there is no link with synaptic.
That is correct.  I agree that it is likely that the problems are the same, but it is possible they are not.  Why would you get a GPG error in addition to whatever problem your having with Synaptic/Apt and Lynx?  Even if the problems aren't related, you still should fix the GPG problem.

What message do you get when you type:
```
lynx 127.0.0.1
```

---

### Post by daydan on 2007-07-28
daniel@standbox86:~$ lynx 127.0.0.1 > x.txt

daniel@standbox86:~$ cat x.txt 

Recherche 127.0.0.1 premier
Recherche localhost:4001
Connexion HTTP à localhost:4001
Alerte! : Impossible d'établir une connexion à l'hôte distant

lynx : accès impossible au fichier de départ [http://127.0.0.1/](http://127.0.0.1/)
daniel@standbox86:~$ 

if i translate just the french message

Looking up 127.0.0.1 first
searching for localhost:4001
Connexion HTTP to localhost:4001
Alert! : Impossible to connect to the host

lynx : impossible to acces file of start [http://127.0.0.1/](http://127.0.0.1/)

---

### Post by Pragmatist on 2007-07-28
This guy had the exact same problem:
[https://answers.launchpad.net/ubuntu/+question/6719](https://answers.launchpad.net/ubuntu/+question/6719)

Unfortunately, he didn't find out the cause since he solved his problem by reinstalling Ubuntu.  The person helping him felt it has something to do with port 4001.  I agree, and I think it is some proxy or firewall issue.

---

### Post by daydan on 2007-07-28
i have a file :
# /etc/default/anon-proxy

# the local port to listen on
# remember to set $HTTP_PROXY and $http_proxy accordingly
PORT="4001"

# list of cascades and/or mixes, seperated by semicolons
# see [http://anon.inf.tu-dresden.de/status.php](http://anon.inf.tu-dresden.de/status.php) for a list
# 80.237.206.62:443; 80.237.206.62:6544; mix.inf.tu-dresden.de:6544;
# mix.inf.tu-dresden.de:443; mix.inf.tu-dresden.de:80;
# mix.inf.tu-dresden.de:22; 212.112.232.175:36544; 212.112.232.175:80;
# 212.112.232.175:443; 80.237.152.53:6544; 80.237.152.53: 443;
# 80.237.152.53:80; 217.10.13.163:6544; 141.76.1.123:16544;
# 141.76.1.123:80; 141.76.1.123:443;
CASCADE="212.112.232.175:36544"

# command-line options passed to proxytest
OPTIONS="-a -d -j -n $CASCADE -p $PORT"


it seems the problem may come from here. What could i change to come back to former preferences.?

i also checked this : 
root@standbox86:/var/log/apache# echo $HTTP_PROXY 
[http://localhost:4001](http://localhost:4001)

---

### Post by daydan on 2007-07-28
ok, lynx is working
i had to uninstall anon-proxy with synaptic
and in the terminal
root@standbox86:~# echo $http_proxy 
[http://localhost:4001](http://localhost:4001)
root@standbox86:~# http_proxy= 
root@standbox86:~# echo $http_proxy 

root@standbox86:~# HTTP_PROXY= 
root@standbox86:~# echo $HTTP_PROXY

root@standbox86:~# 

The problem persist with synaptic.

EDIT ; the problem get solved after a reboot.
HOW TO SOLVE the problem with 4001 localhost ?
Uninstall Anon-proxy with synaptic, set $http_proxy variable empty, and reboot.

thanks for help

---

