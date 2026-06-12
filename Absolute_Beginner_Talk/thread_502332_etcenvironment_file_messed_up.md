---
title: "/etc/environment file messed up?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by kitty500cat on 2007-07-16
I had had some problems downloading the multiverse and universe repositories.  It always failed at download the Translation-en_US files.  I think my /etc/environment file is somehow messed up.  Could somebody please look at it and tell me if it needs modification?  Thanks.

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
```

Note: I live in the United States.

---

### Post by forestpixie on 2007-07-16
Mines exactly nearly the same :D - just live in the UK

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_GB.UTF-8"
```

is your sources.list ok?

---

### Post by kitty500cat on 2007-07-16
The result of $ sudo cat /etc/apt/sources.list
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse

```
It looks like the last three lines are unnecessary; would that cause a problem?

Thanks for your help so far.

---

### Post by forestpixie on 2007-07-16
not sure - you could try commenting them out and try to update

backup the file

```
cd /etc/apt
```

```
sudo cp sources.list sources.bak
```

then

```
gksudo gedit /etc/apt/sources.list
```

put ## in front of each line, then save

then update 
```

sudo apt-get update

```

Edit - When it fails what does it actually say? Can you post the output of the apt-get update command when you do it.

---

### Post by kitty500cat on 2007-07-16
I did sudo apt-get update, and it updated with no problems whatsoever.  I had actually edited my /etc/environment file sometime before I posted it here; I think it was messed up before but is straightened out now.

Thanks for your help! :)

---

### Post by forestpixie on 2007-07-16
not a problem

---

