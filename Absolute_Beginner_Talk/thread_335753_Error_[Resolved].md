---
title: "Error [Resolved]"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-01-10
I tried to install a .deb package and I got this error....[IMG]http://www.furnbach.com/image/Screenshot.jpg[/IMG]

Hamm

---

### Post by taurus on 2007-01-10
Make sure you have enable both universe & multiverse in /etc/apt/sources.list by removing the # in front of them.  Then, run it from a terminal and see what happens (don't forget to close synaptic first though).

Applictions -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install webmin
```

---

### Post by Hamm on 2007-01-10
> **taurus said:**
> Make sure you have enable both universe & multiverse in /etc/apt/sources.list by removing the # in front of them.  Then, run it from a terminal and see what happens (don't forget to close synaptic first though).

Applictions -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install webmin
```

I am a real noob at linux and where would I find this "/etc/apt/sources.list" to do the removing?

---

### Post by moshuptrail on 2007-01-10
oddly enough, its located at /etc/apt/sources.list
so maybe the question is how to edit it and remove the #s

two ways:
for the brave: open a terminal and type sudo gedit /etc/apt/sources.list

another way, not quite as flexible but will work:
System > Administration > Software Properties
Check all the boxes

---

### Post by Hamm on 2007-01-10
I got it finally, thanks for the help....;)

---

