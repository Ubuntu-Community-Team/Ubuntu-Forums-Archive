---
title: "bad line in source list"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by oldgarol on 2007-03-04
Hi All 
I need help to remove a bad line in my source list which is preventing Adept and Add/Remove programs from working. 
This is the message I get:

graham@Laura:~$ sudo apt-get update
E: Type &#8216;[http://archive.canonical.com/ubuntu&#8217;](http://archive.canonical.com/ubuntu&#8217;) is not known on line 1 in source list /etc/apt/sources.list

I get this message with all the commands I have tried. (I am very new to this)

---

### Post by mahy on 2007-03-04
Please post the contents of your /etc/apt/sources.list file. For example like this (open terminal and run):

```
cat /etc/apt/sources.list
```

---

### Post by Kateikyoushi on 2007-03-04
Remove the ' from the end of the line.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```

---

### Post by Cruncher on 2007-03-04
No, instead, all lines in /etc/apt/sources.list containing info need to start with the keyword "deb" or "deb-src", which seems to be missing in your case.
An example would be:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

Cheers,
Cruncher

---

### Post by Kateikyoushi on 2007-03-04
How do you know he is using edgy ?

---

### Post by Cruncher on 2007-03-04
Well, it was just an example. The important part is the preceding "deb".
And in case your /etc/apt/sources.list is too garbled to recover, [here]("http://www.ubuntu-nl.org/source-o-matic/") is a nice tool that can autogenerate one for you.

---

### Post by jvc26 on 2007-03-04
It would help to see the sources.list in question if none of the above methods have worked -
```

cat /etc/apt/sources.list

```
Il

---

