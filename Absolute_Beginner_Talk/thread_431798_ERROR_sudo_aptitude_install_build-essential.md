---
title: "ERROR: sudo aptitude install build-essential"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by El Gabito on 2007-05-03
I get the error at the end when running

```
sudo aptitude install build-essential
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  binutils cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc gcc-4.1 libc6-dev libmudflap0-dev libstdc++6-4.1-dev linux-libc-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc gcc-4.1 libc6-dev libmudflap0-dev libstdc++6-4.1-dev linux-libc-dev
0 packages upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.8MB of archives. After unpacking 49.2MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
E: Failed to fetch cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/b/binutils/binutils_2.17.20070103cvs-0ubuntu2_i386.deb: MD5Sum mismatch

```

Any suggestions? Trying to get gcc...

---

### Post by taurus on 2007-05-03
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the line (near the top of the file) that has cdrom in it to comment it out.  Save it and then run

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by jkeyes0 on 2007-05-03
can you post the contents of your /etc/apt/sources.list file?

---

### Post by Cypher on 2007-05-03
Your Feisty CD is listed as a repository in the file /etc/apt/sources.list and you don't have it inserted. So
```

gksudo gedit /etc/apt/sources.list

```
and add a "#" before the Fesity Fawn CD entries, then do
```

sudo apt-get update

```
and re-do the install command..

---

### Post by El Gabito on 2007-05-03
I'm running ubuntu server btw...

```
The program 'gksudo' is currently not installed.  You can install it by typing:
apt-get install gksu
bash: gksudo: command not found

```


```
apt-get install gksu
```

Goes fine until a ways into it...

```
Get:84 http://us.archive.ubuntu.com feisty/main libgksu2-0 2.0.3-3ubuntu5 [62.1kB]
Get:85 http://us.archive.ubuntu.com feisty/main gksu 2.0.0-1ubuntu3 [52.6kB]
Fetched 2868kB in 56s (51.1kB/s)
Failed to fetch cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/d/defoma/defoma_0.11.10_all.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/g/gcc-4.1/cpp-4.1_4.1.2-0ubuntu4_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I used vi to open the sources.list:

```
#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

---

### Post by Cypher on 2007-05-03
OK..then..
```

sudo vi /etc/apt/sources.list

```
Scroll down to the "deb cdrom:" line..with the cursor on the "d", hit "i" to insert, enter "#", and then hit ESC. Then type ":wq" which will write and quit. Now re-do the "update" command..

---

### Post by taurus on 2007-05-03
Put a # sign in front of the 4th line.

```
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```

---

### Post by El Gabito on 2007-05-03
> **Cypher said:**
> OK..then..
```

sudo vi /etc/apt/sources.list

```
Scroll down to the "deb cdrom:" line..with the cursor on the "d", hit "i" to insert, enter "#", and then hit ESC. Then type ":wq" which will write and quit. Now re-do the "update" command..

HA! yeah, I missed that part - I was doing it as you posted. 

Thanks, you guys rock.

---

### Post by Cypher on 2007-05-03
Glad we could help..:)

---

