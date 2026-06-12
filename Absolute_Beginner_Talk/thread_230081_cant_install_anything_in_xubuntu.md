---
title: "cant install anything in xubuntu"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-05
I just installed xubuntu and I just can´t find a way to install xmms or any other player that i could listen mp3´s. Why doest sudo apt-get install xmms work in xubuntu? it just says couldn´t find package.

---

### Post by taurus on 2006-08-05
You need to enable both universe and multiverse in /etc/apt/sources.list first!!!  So, open a terminal and edit it by removing the # sign in front of all the lines that end up with universe & multiverse...

```

sudo nano /etc/apt/sources.list

```
Then, save it and install it with

```

sudo apt-get update
sudo apt-get install xmms

```

---

### Post by aysiu on 2006-08-05
Sounds as if you need a new sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Do that and then ```
sudo aptitude update
sudo aptitude install xmms
```

---

### Post by vaazu on 2006-08-05
thanks alot
oh by the way how can I uninstall xmms if I want?

---

### Post by aysiu on 2006-08-05
```
sudo aptitude remove xmms
```

---

### Post by ketnoe on 2006-08-05
cant delete my own post?

---

### Post by vaazu on 2006-08-05
> **taurus said:**
> You need to enable both universe and multiverse in /etc/apt/sources.list first!!!  So, open a terminal and edit it by removing the # sign in front of all the lines that end up with universe & multiverse...

```

sudo nano /etc/apt/sources.list

```
Then, save it and install it with

```

sudo apt-get update
sudo apt-get install xmms

```

If I do the sudo apt-get update it says E: Type 'uncomment' is not known on line 10 in source list /etc/apt/sources.list

---

### Post by aysiu on 2006-08-06
You shouldn't have the word *uncomment* in your /etc/apt/sources.list.

To uncomment a line, you just remove the # sign in front of the line.

**Commented**: ```
#deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
```

**Uncommented**: ```
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
```

---

### Post by jimmygoon on 2006-08-06
> **vaazu said:**
> If I do the sudo apt-get update it says E: Type 'uncomment' is not known on line 10 in source list /etc/apt/sources.list

You removed the comment from the comment telling you to remove the comment signs.

Basically everything below the sentences are special lines to tell ubuntu where to find software. If you have a '#' in front of it, it won't read it. Those sentences at the top will throw it off, so you have to keep the '#' in front of them, but for the rest of the "special lines" that begin with 'http'. you should remove the '#' so that you can install more software.

---

