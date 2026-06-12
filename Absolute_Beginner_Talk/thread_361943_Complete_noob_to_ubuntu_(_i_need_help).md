---
title: "Complete noob to ubuntu ( i need help)"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by CircaSurvivor on 2007-02-15
how do you enable the Universe Repository?  I read that you are supposed to edit /etc/apt/sources.list but i dont understand how to do that

---

### Post by nickoli_02 on 2007-02-15
To enable restricted repositories, open a terminal (Applications -> Accessories) then type this:

```
kgsudo gedit /etc/apt/sources.list
```

then remove the #'s that are before the lines of "deb <url>" to uncomment these repositories.

---

### Post by CircaSurvivor on 2007-02-15
now it says "couldnt find package firestarter" (im trying to install it)
the firestarter web site says i can get it from the universe repository.

---

### Post by Spike-X on 2007-02-15
You need to do

```
sudo apt-get update
```

first.

---

### Post by ramjet_1953 on 2007-02-15
Navigate to:

[COLOR="Blue"]System>Administration>Synaptic Package Manager
[/COLOR]
Enter your [COLOR="Red"]Administrator Password[/COLOR], when prompted. ie the password that you use to log into your session with.

Navigate to:

[COLOR="Blue"]Settings>Repositories[/COLOR]

Click on any boxes that don't have an "[COLOR="Red"]X[/COLOR]" in them.

Also check on the drop-down menu if there is a [COLOR="Red"]server[/COLOR] close to you, which will give you faster downloads.

Enjoy!

Regards,
Roger 8-)

---

### Post by CircaSurvivor on 2007-02-15
sweet, thanks guys, i am very new to this system :)

---

