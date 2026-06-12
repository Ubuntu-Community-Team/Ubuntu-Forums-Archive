---
title: "Can't install any software after delete /var/cache/archives!"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by jaywee on 2007-05-03
several days ago I was too boring to do anything else, so I delete all the files under /var/cache/apt/archives, because it is said all these files are installed software packages, I thought they are useless. Then here comes a big problem, when I type apt-get install * or apt-get update, the terminal will give the hint that could not open lock file /var/cache/apt/archives/lock - open, and unable to lock the download directory,
I do

```
sudo mkdir /var/cache/apt/archives
sudo mkdir /var/cache/apt/archives/lock
sudo aptitude update
sudo aptitude upgrade
```

as taurus said. now I can do

```

sudo apt-get update
```

and


```
sudo apt-get dist-upgrade
```

but, there is still a problem that I can't install any software ,when I do


```
sudo apt-get install *
```

I got the message:

```

E:could not open lock file  /var/cache/apt/archives/lock - open(21 is a directory)
E:unable to lock the download directory!
```

so who can help to fix that??
thanks!!

---

### Post by ggaaron on 2007-05-03
Tried making this file? It is empty - it just has to be there.

use gedit, kate, vim or any other editor - just remember you have to have root rights to write there.

I think it should help.

---

### Post by Cypher on 2007-05-03
do
```

sudo rm -rf /var/cache/apt/archives/lock

```
and then do
```

sudo apt-get update

```
and see if the install command will work. You created a directory for "lock" which should actually just be a file..

---

### Post by taurus on 2007-05-03
What are you trying to install?  You need to specify the name of the program.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Carlos Santiago on 2007-05-03
It seems that lock must be a file, not a directory. So make:
```
sudo rm -rf /var/cache/apt/archives/lock
```
To delete the directory. Then make
```
sudo touch /var/cache/apt/archives/lock
```
To create an empty file

---

### Post by Cypher on 2007-05-03
> **Carlos Santiago said:**
> It seems that lock must be a file, not a directory. So make:
```
sudo rm -rf /var/cache/apt/archives/lock
```
To delete the directory. Then make
```
sudo touch /var/cache/apt/archives/lock
```
To create an empty file

I'm just curious...**ggaaron** and I suggested the exact same thing you suggested shortly after the OP made the topic, over a hour ago. Why would you reply with the same things we already suggested? Suggesting something else makes sense, but the same?

---

