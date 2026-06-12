---
title: "cant open rars"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2006-09-21
What do I need to open .rars?

---

### Post by Kurdt on 2006-09-21
Download rar for linux from [www.rarlabs.com](www.rarlabs.com) and compile it, you will be able to open rars with file-roller

---

### Post by DiJEH on 2006-09-21
hoow do you compile it?

---

### Post by Kurdt on 2006-09-21
at the prompt:

```
tar zxvf rarlinux-3.6.0.tar.gz
```

```
cd rar/
```

```
sudo make
```

```
sudo make install
```

If you get anything like make not found or something you need to install it with

```
sudo apt-get install make
```

---

### Post by Billquinn1 on 2006-09-21
Is this different / better than the non free version in the ubuntu repos?

Bill.

---

### Post by skymt on 2006-09-21
> **Billquinn1 said:**
> Is this different / better than the non free version in the ubuntu repos?

Bill.

It's the same thing.

---

