---
title: "Powerout messed up my Dapper upgrade"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by wat3r on 2006-06-10
I was upgrading to Dapper yesterday, when I had a powerout in the middle of the installation. Is there any way to upgrade again?

---

### Post by adam.tropics on 2006-06-10
Oh dear! More info would help people help you, such as some basics like, what happens now if you try to boot? If it does, then you could just do the dist-upgrade again.

---

### Post by wat3r on 2006-06-10
It boots fine, but it looks kind of half-done, if you know what I mean. How do I do the dist-upgrade again?

---

### Post by adam.tropics on 2006-06-10
You do mean upgrade rather than install right?
If so, and you have a reasonable net connection,open a terminal and

```
sudo gedit /etc/apt/sources.list
```

Check the sources are for dapper. If for some reason they are not, replace the word breezy with dapper on all the repos.
```

sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by wat3r on 2006-06-12
I did this, and I think the update was almost done, because all it did was update Firefox.

---

### Post by adam.tropics on 2006-06-12
In a terminal type

```
lsb_release -ds
```

What does that give you?

---

### Post by wat3r on 2006-06-17
I tried to reboot after installing again, and now it works just fine :) Thanks for the help ;)

---

