---
title: "Repo's packet manager not working..."
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-03
I've just installed ubuntu edgy 6.10 on another laptop and the packet manager don't seem to be working fully.

I've tried to download duplicity and firestarter, it can't find the packages. Also tried sudo apt-get duplicity, can't find it there either.

Why?? :confused: :confused: :confused:

---

### Post by taurus on 2006-12-03
You need to enable both universe & multiverse in /etc/apt/sources.list by removing the # in front of those lines...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install firestarter
```

---

### Post by linuxbun on 2006-12-03
That sorted it, cheers!! :)

---

### Post by taurus on 2006-12-03
> **linuxbun said:**
> That sorted it, cheers!! :)
Great!  ;)

---

