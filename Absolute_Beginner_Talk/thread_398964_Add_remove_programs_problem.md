---
title: "Add remove programs problem"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-04-01
When i run the update manager, it says that not all updates can be installed, and i should update the distrubution (i'm on edgy). Is this a good idea?

---

### Post by mills on 2007-04-01
does it say what updates cant be installed?

---

### Post by ajeffreys on 2007-04-01
Does this help?

[[IMG]http://img150.imageshack.us/img150/8243/screenshot1ks5.th.png[/IMG]](http://img150.imageshack.us/my.php?image=screenshot1ks5.png)

Thanks

---

### Post by ajeffreys on 2007-04-02
Bump

---

### Post by zvacet on 2007-04-02
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by ajeffreys on 2007-04-02
But will that upgrade it to feisty if i do all this?
Thanks,
Ajeffreys

---

### Post by Majorix on 2007-04-02
Yes it will. Alternatively, instead of what zvacet said, you can use

```
sudo apt-get update && sudo apt-get dist-upgrade
```

It will do the same thing, but what I said is more common.

---

### Post by ajeffreys on 2007-04-02
Thankyou very much for all of the help, :)

---

### Post by zvacet on 2007-04-02
I use aptitude command because with it you download program and dependencies wich is not  case if you use apt-get.You make me thinking about distro upgrade from one reason only.in previous realeses massage for distro upgrade was  in update manager when final version is out.I don´t know if anything is changed.Maybe you will recive updates for Edgy wich will make more easy and smooth to upgrade to Feisty.

---

