---
title: "XGL Problemss!!!!"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-04-24
:confused: 

Hello

I wanted to install XGL on my Edgy but if I input command : sudo apt-get install xserver-xgl in terminal write me following: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

Is it any other way or command line wich install me xserver-glx package or is this somethin related to graphic drivers or card. I use Nvidia mx 440 graphic acleration with Nvidia.. 8776-pkg1 drivers instaled???????

Thanx 

Urko

---

### Post by lamalex on 2007-04-24
do you have univserse enabled? I've never seen that before, xgl installed fine for me.

---

### Post by ajgreeny on 2007-04-24
Have you enabled the universe and multiverse repos?  In dapper xserver-xgl is in the universe repository, so I suspect that it is also there for edgy.
EDIT>  OK I'm not quick enough.

---

### Post by Urko on 2007-04-24
How can i enable universe and multiverse responsitories?????

sorry I am new in Linux:confused:

---

### Post by lamalex on 2007-04-24
system >a administration > software sources > community maintained software (universe)
enable and reload then try again.

---

### Post by ajgreeny on 2007-04-24
Probably easiest to open synaptic and then go to *Settings>Repositories* and enable them in the list of repositories shown there.

---

