---
title: "synaptic PM is *messed freakin up*"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-21
...Ok, whenever I open up synaptic package manager, I get a small white blank box in the middle of my screen, that has no markings on it at all....and only goes away if I log off....


what do you think it is and how can i get rid of it??? help!

---

### Post by thelatinist on 2007-12-21
No clue what it is, but why don't you try reinstalling synaptic?

```
sudo apt-get update
sudo apt-get --reinstall synaptic
```

---

### Post by B34ST1Y on 2007-12-21
```
b34st1y@zer0cool:~$ sudo apt-get --reinstall synaptic
E: Invalid operation synaptic
b34st1y@zer0cool:~$ 

```

---

### Post by spiderbatdad on 2007-12-21
do you have any sources listed in /etc/apt/sources.list?  that is any that have no # in front of them.

---

### Post by nowshining on 2007-12-21
sudo apt-get install synaptic

also the box in the middle of the screen is most likely the passworkd dialog box popping up asking for ur password, u need a administrator pw to access synaptic and install items and or remove them.

do u have compiz on, if so, try turning it off and try again

right click change background,

last tab.

---

### Post by philinux on 2007-12-21
That should be

sudo apt-get install --reinstall synaptic

---

### Post by thelatinist on 2007-12-21
> **philinux said:**
> That should be

sudo apt-get install --reinstall synaptic

Yes, I'm sorry.  Just a typo. It should be

```
sudo apt-get install --reinstall synaptic
```

---

### Post by Incense on 2007-12-21
Do you have compiz enabled? Maybe disable desktop effects and try it again. Sounds like something CF would do....

---

