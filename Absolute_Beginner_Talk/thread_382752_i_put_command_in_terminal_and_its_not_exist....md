---
title: "i put command in terminal and its not exist...?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-12
i dont remember exactly which commands give me the messgae: "command not exist .  but the last one was  : "sudo apt-get install cowsay". it happends allot of time until now maybe i missed something? remember im totally newbie

---

### Post by taurus on 2007-03-12
What happens when you run this command?

```
sudo aptitude update
```

---

### Post by rjfioravanti on 2007-03-12
could you try running a problematic command again and posting here what the error message was exactly?

---

### Post by fanny on 2007-03-12
i did TAURUS command and there was an fast update

---

### Post by fanny on 2007-03-12
fanny@fanny-desktop:~$ sudo apt-get install cowsay
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cowsay
fanny@fanny-desktop:~$ sudo apt-get install cowsay
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cowsay
fanny@fanny-desktop:~$

---

### Post by rjfioravanti on 2007-03-12
ok so your command is find, but you are telling it to find a package in the ubuntu repositories called cowsay, which apparently doesn't exist

I've never heard cowsay, can you give some information what it is you are trying to install, or maybe a link to instructions you have been following

it is possible you have to add a new repository server to your list of sources. You can find this list of sources on your system at

/etc/apt/sources.list

Its just a text file with different url's it looks to, to download software using apt-get

and right now, no url exists in that list, with cowsay available for download

---

### Post by fanny on 2007-03-12
i checked this folder (/etc/apt/sources.list ) its empty...

---

### Post by rjfioravanti on 2007-03-12
Try this, if it doesnt work post the error message

```

sudo gedit /etc/apt/sources.list

```

---

### Post by fanny on 2007-03-12
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by taurus on 2007-03-12
> **rjfioravanti said:**
> Try this, if it doesnt work post the error message

```

sudo gedit /etc/apt/sources.list

```

Should use gksudo.

```
gksudo gedit /etc/apt/sources.list
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by rjfioravanti on 2007-03-12
now can you give us some information about 'cowsay'

where did you find out about it, do you have a link?

---

### Post by fanny on 2007-03-12
here is the link
[http://www.ubuntuforums.org/showthread.php?t=382010](http://www.ubuntuforums.org/showthread.php?t=382010)

---

### Post by fanny on 2007-03-12
i tried now  fanny@fanny-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:14047): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
fanny@fanny-desktop:~$

---

### Post by Rui Pais on 2007-03-12
hi
cowsay is in universe, which is not enabled on your sources.list

change the line:
> **# **deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
to:
> deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

redo:
```
sudo aptitude update
```
and  then you could install it.

---

### Post by fanny on 2007-03-12
sorry but i dont what you mean change the line.

---

### Post by Rui Pais on 2007-03-12
> **fanny said:**
> sorry but i dont what you mean change the line.

your english is even worst then mine... ;)
don't know if i quiet understand what you are saying. 

If you don't undersant what i suggest, do:
```
gksudo gedit /etc/apt/sources.list
```
and delete the symbol **#** from the beginning of the line that mention universe.
save it. Then do:
```
sudo aptitude update
``` 
```
sudo aptitude install cowsay
```

---

### Post by steve.horsley on 2007-03-12
You can add the extra repositories this way:
[http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29)

---

