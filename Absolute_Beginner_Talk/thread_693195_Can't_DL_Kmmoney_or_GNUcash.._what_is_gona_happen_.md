---
title: "Can't D/L Kmmoney or GNUcash.. what is gona happen next!?!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by USFMD82 on 2008-02-10
since upgrading to 7.10 I ahve had nothing but problems.. this time I have decided I need a budgeting tool.

I go to d/l Kmymoney, after the .deb is dl to pen it up I get the error of dependecies or soemthign with KDElib4 so I go to Synaptic and type that in.. nothing comes up.. I try many other things and gave up so I go to GNUcash

Download GNUcash deb and then I keep getting the error dependency on GNUcash..

I woudl love ot revert back to 7.04 til the next one comes out.. but how do I do that... if I cant fix this stuff Im gonna go nuts!! lol Im still on board the linux train however just had a huge bout with malware on my windows OS

---

### Post by neurostu on 2008-02-10
To install GNUCash simply add the following line to: /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu gusty main restricted universe multiverse

```
Then execute
```

sudo aptitude update
sudo apt-get install gnucash

```

---

### Post by USFMD82 on 2008-02-11
Thank you!

This is gonna sound stupid how do I add the line to the sources.list?

also any idea how I can fix the KMymoney problem, at work now I will update later if it works. I cant tell but the screenshots make me think Kmymoney is a bit better as far as the interface.. I keep hearing both sides so I wanted to try both and decide for myself

---

### Post by neurostu on 2008-02-11
open a terminal

```

$ sudo gedit /etc/apt/sources.list

```

Then add the line to the bottom

---

### Post by neurostu on 2008-02-11
As far as KMyMoney, the best way to install it would be using APT. it takes care of all dependencies for you. Just google for "Install KMyMoney using apt"

---

### Post by USFMD82 on 2008-02-11
OK followed your steps.. here is what it says in Sources.list

```
deb http://archive.ubuntu.com/ubuntu/ gutsy restricted
deb-src http://archive.ubuntu.com/ubuntu gusty main restricted universe multiverse
```

After I close that and run the other commands I get this..
```
 sudo aptitude update

Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gusty Release.gpg
Hit http://archive.ubuntu.com gutsy Release
Ign http://archive.ubuntu.com gusty Release   
Hit http://archive.ubuntu.com gutsy/restricted Packages
Ign http://archive.ubuntu.com gusty/main Sources
Ign http://archive.ubuntu.com gusty/restricted Sources
Ign http://archive.ubuntu.com gusty/universe Sources
Ign http://archive.ubuntu.com gusty/multiverse Sources
Err http://archive.ubuntu.com gusty/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gusty/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gusty/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gusty/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Fetched 1B in 1s (1B/s)  
Reading package lists... Done

```

```
sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnucash

```

Trying KMymoney Thanks for the help!

---

### Post by USFMD82 on 2008-02-11
Here is the KMymoney problem

```
 sudo apt-get install build-essential
[sudo] password for timber:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
_timber@ubuntu:~$ sudo apt-get build-dep kmymoney2_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gusty_main_source_Sources - open (2 No such file or directory)
timber@ubuntu:~$ 
```

---

### Post by USFMD82 on 2008-02-14
Found my problem, and fixed it, I went into the Software sources, and oddly there was only one box clicked, (in other words I was unable to search for other packages, I clicked htem all and now it works!! Thanks for your help!! Now on to figuring out which one I like more!

---

