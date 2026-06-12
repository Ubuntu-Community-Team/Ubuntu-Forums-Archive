---
title: "Airpwn Dependencies?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
I got the libnet1-dev, but what's the LORCON thing it needs? And how many more dependencies after this are there gonna be?

---

### Post by joshrobinson on 2008-04-05
your going to have to compile lorcon from source

```
sudo apt-get install subversion
```

```
svn co https://802.11ninja.net/svn/lorcon/trunk/ 
```
hit t when it asks about certificate

```
cd trunk
```

```
./configure
make
make install
```

and i have no idea how many more dependencies there will be

---

