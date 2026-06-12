---
title: "Synapic Problem with Proxy"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by unknownlaopoet on 2007-06-21
I had set up my proxy wrong earlier, but after changing proxy in pereferences it still sees the old proxy when i try to update

here is what i did 



usr@usr:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
18% [Connecting to 16.101.160.111 (16.101.160.111)] [Connecting to 16.101.160.1
usr@usr:~$ sudo gedit /etc/apt/apt.conf
Password:
use@usr:~$
use@usr:~$

my apt.conf file shows which is the correct proxy

Acquire::http::Proxy "16.111.160.101";


is there another file that i should edit to fix this

---

### Post by unknownlaopoet on 2007-06-21
can anyone help am i in wrong thread?

---

### Post by zwchten on 2007-06-21
I am using Feisty too but I don't have the file you mentioned /etc/apt/apt.conf 

You can try go into Synaptic -> Settings -> Preferences -> Network, and select Manual Proxy Configuration, filling in your preferred proxy there.

Hope that works.

---

### Post by unknownlaopoet on 2007-06-21
> **zwchten said:**
> I am using Feisty too but I don't have the file you mentioned /etc/apt/apt.conf 

You can try go into Synaptic -> Settings -> Preferences -> Network, and select Manual Proxy Configuration, filling in your preferred proxy there.

Hope that works.


that was the first thing i did.. and yes i did change it.. which is why i dont understand whats going on... it doesnt use the new proxy i set and only uses the first one... also i tried restarting a few times.. which did not help

---

