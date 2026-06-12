---
title: "No Alien"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by w00ten on 2006-07-11
I'm trying to install alien so that I can convert rpm files. Heres the problem. when I run apt-get... it doesn't work!!! says it can't find the package. I then headed to synaptics and its not there either... so needless to say im rather stumped. when I try to download it off of the package area of the ubuntu site, that doesn't work either, it gets errors on the install. any help would be appreciated. Thanks.

---

### Post by T700 on 2006-07-11
Try this first:

```
sudo aptitude update
```

then

```
sudo aptitude install alien
```

Paul

---

### Post by taurus on 2006-07-11
Perhaps you need to comment out by removing the # in front of lines for universe & multiverse.  Open a terminal, Applications -> Accessories -> Terminal, and type
```

sudo gedit /etc/apt/sources.list

```
Save it and run
```

sudo apt-get update
sudo apt-get install alien

```

---

