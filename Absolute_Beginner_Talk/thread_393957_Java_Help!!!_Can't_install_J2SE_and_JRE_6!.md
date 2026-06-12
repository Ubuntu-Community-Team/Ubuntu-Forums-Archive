---
title: "Java Help!!! Can't install J2SE and JRE 6!"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by c.gymer on 2007-03-26
Hey folks.

I'm having real problems getting Java. I've run some searches and nothing has worked so far so here I am asking for some help!

I'm a total noob so please be gentle.

I can't get either J2SE or JRE 6 to install. I've followed the Ubuntu wiki guide and the following appears when I try to install J2SE, with the code "sudo aptitude install sun-java6-jre sun-java6-plugin".


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "sun-java6-plugin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


What am I doing wrong here?

Also, when I try to install JRE 6 using the guide, I can't install fakeroot (sudo apt-get fakeroot), and recieve the message:

E: Invalid operation fakeroot


Again, what am I doing wrong (or not doing, if thats the case?).


I'm running edgy on a Dell inspiron 6400 with a 1.83 core duo processor and 1 gig of RAM.


Thanks in advance, chaps/chapettes.




[www.myspace.com/noontheband](www.myspace.com/noontheband)
[www.noontheband.com](www.noontheband.com)

---

### Post by taurus on 2007-03-26
Have you enabled both universe and multiverse in /etc/apt/sources.list?  Edit /etc/apt/soures.lis with

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all lines with deb at the beginning.  Save the change and run

```
sudo aptitude update
```
Now, see if you can install java and the plugins again.

p.s.  I believe the repos only have version 1.5.  If you want to use 1.6, you need to download the .bin and install it by hand.

---

### Post by camz on 2007-03-26
Try taurus' method first, as Java Runtime Environment 6 is a newer version, but if this all fails, go into Applications>Add/Remove and scroll down until you find Java Runtime Environment 5. This will work fine with games such as RuneScape, so hopefully it will work with whatever you need.

Hope I was of help,
Camz

---

