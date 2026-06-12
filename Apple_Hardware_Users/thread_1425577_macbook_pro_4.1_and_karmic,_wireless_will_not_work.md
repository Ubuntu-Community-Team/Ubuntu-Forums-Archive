---
title: "macbook pro 4.1 and karmic, wireless will not work"
date: 2010-03-09
forum: Apple Hardware Users
---

### Post by slaytalera on 2010-03-09
Hey guys, i just installed Karmic on my Macbook pro 4.1 and i cant get wireless to work, ive searched and it says it should work out of the box, after activating the broadcom driver, problem is that it will not find the driver when i go to hardware drivers.  The card itself is working, infact i am on it now typing this from OS X.  How can i get Ubuntu to see my drivers?

---

### Post by linuxopjemac on 2010-03-09
```
sudo apt-get bcmwl-kernel-source
```

Be sure to have an internet connection (wired)

---

### Post by slaytalera on 2010-03-09
> **linuxopjemac said:**
> ```
sudo apt-get bcmwl-kernel-source
```Be sure to have an internet connection (wired)


it gives me an "invalid operation" error, i copied it exactly as you typed it


EDIT: nevermind, used an exernal wireless card to connect and activate the driver, thanks!

---

### Post by linuxopjemac on 2010-03-10
sorry, my bad. It should have been:
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by Atilana on 2010-03-10
check if the wireless connection is able, turno off the computer check the wire conection.

---

