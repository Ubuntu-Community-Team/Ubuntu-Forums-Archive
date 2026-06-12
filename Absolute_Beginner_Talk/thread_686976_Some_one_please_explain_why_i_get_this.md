---
title: "Some one please explain why i get this"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by uruk912 on 2008-02-03
Ive been doing this all day and it dosnt work can some one tell me why i get this error when i try to install the drivers for my wifi.
[IMG]http://i26.tinypic.com/mwti7l.png[/IMG]

---

### Post by bruce89 on 2008-02-03
You have no C standard library installed.

```

sudo aptitude install libc6-dev

```

---

### Post by taurus on 2008-02-03
And

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Majorix on 2008-02-03
> **bruce89 said:**
> You have no C standard library installed.

```

sudo aptitude install libc6-dev

```

I have never done it manually but build-essential should (as far as I know) install that package for you automagically.

---

### Post by bruce89 on 2008-02-03
> **Majorix said:**
> I have never done it manually but build-essential should (as far as I know) install that package for you automagically.

It does, but it also installs some other packages that aren't needed such as *g++*, *dpkg-dev* and *make*.

---

### Post by uruk912 on 2008-02-03
Sorry the pic is so big didnt think it was that big well anyway he is a new prob.

im at the modprobe thing and i type
sudo modprobe ath_pci and it makes no response not an error or anything is that how its soposta be?

---

### Post by uruk912 on 2008-02-03
Bump some one answer the question above sorry for double post

---

