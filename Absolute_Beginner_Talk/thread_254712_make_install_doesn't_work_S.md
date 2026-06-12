---
title: "make install doesn't work :S"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Izuil on 2006-09-10
when i try:

```
sudo make install
```

it gives me: ```
sudo: make: command not found
```

and with just:

```
make install
```

it gives me: ```
bash: make: command not found
```

What to do?

---

### Post by elettronicha on 2006-09-10
You need to install the essential to compile. Please read the wiki for more infos ;)

> sudo apt-get install build-essential

---

### Post by jcrnan on 2006-09-10
sudo apt-get install buildessential

---

### Post by taurus on 2006-09-10
> **jcrnan said:**
> sudo apt-get install buildessential
WRONG!!!  Look at the post just above yours...  :rolleyes:

---

### Post by az on 2006-09-10
If you are not on the internet, those packages can be found on the install cd.

Just pop the cd in the drive when you are at the desktop.  That will start the package manager.  Search for build-essential and install it.


The linux-headers are there too, if you need to build a driver for your kernel.

---

### Post by Izuil on 2006-09-10
thanks alot guys :D

Works now! :)

---

