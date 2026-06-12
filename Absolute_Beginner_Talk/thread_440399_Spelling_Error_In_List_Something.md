---
title: "Spelling Error In List Something?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-11
Well ive been told to do something like.


nic@nic-desktop:~$ sudo apt-get update
**E: Type '-e\n' is not known on line 34 in source list /etc/apt/sources.list**

How do I fix this?

---

### Post by pizzutz on 2007-05-11
post the output of this command:

```
cat /etc/apt/sources.list
```

We should be able to tell you how to modify line 34

---

### Post by LollYouSuckZor on 2007-05-11
> **pizzutz said:**
> post the output of this command:

```
cat /etc/apt/sources.list
```

We should be able to tell you how to modify line 34

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
-e\n## Beryl repository\ndeb http://www.ubuntu.beryl-project.org/ edgy main

sudo tee -a /etc/apt/sources.list
sudo apt-get update

ic
nic
********

lol
okay
******* a
```

---

### Post by RomeReactor on 2007-05-11
Hi. The error is here (in bold):

```
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
**-e\n## Beryl repository\ndeb http://www.ubuntu.beryl-project.org/ edgy main**

sudo tee -a /etc/apt/sources.list
sudo apt-get update

ic
nic
********

lol
okay
******* a
```

From the terminal:

```
gksudo gedit /etc/apt/ources.list
```

and change that line to read

```
# Beryl repository
deb http://www.ubuntu.beryl-project.org/ edgy main
```

Yes, that one line becomes two; and you should delete these lines also:

```
sudo tee -a /etc/apt/sources.list
sudo apt-get update

ic
nic
********

lol
okay
******* a
```

Now save the file, close Gedit, and:

```
sudo apt-get update
```

---

### Post by bobplano on 2007-05-11
> **RomeReactor said:**
> 
```
gksudo gedit /etc/apt/ources.list
```
looks like there are more typos than just in their list. (i mean that in a joking way). just in case you are just copying and pasting though it is ```
gksuo gedit /etc/apt/sources.list
```

---

### Post by RomeReactor on 2007-05-11
There goes my 99.9% perfect spelling record...
:(

---

### Post by pizzutz on 2007-05-12
> **bobplano said:**
> looks like there are more typos than just in their list. (i mean that in a joking way). just in case you are just copying and pasting though it is ```
gksuo gedit /etc/apt/sources.list
```

I don't want to sound mean by any means, but it looks like you both need typing lessons. :)
third times the charm.


```
gksudo gedit /etc/apt/sources.list
```

---

