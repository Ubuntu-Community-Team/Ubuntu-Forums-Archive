---
title: "Problem using add/remove"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Rinaldo on 2008-02-10
I open the add remove app and everything is fine. when I click on something to install it I get the following "The list of applications is not available Click 'reload' to load it. To reload the list you need a working internet connection" when i hit "refresh" some loader things flash up "downloading loader package" is one. then when i try to install the program again the same thing happens.

I am using Ubuntu 7.1

---

### Post by jan quark on 2008-02-10
you have to enable the sources

check if the sources are active

system > administration > software sources

check them all

run

```
sudo apt-get update
```

and try again to install


you can also post the output from

```
cat /etc/apt/sources.list
```

---

### Post by seventhc on 2008-02-10
open a terminal and post the output of this
```

gedit /etc/apt/sources.list

```

---

### Post by Rinaldo on 2008-02-10
> **jan quark said:**
> you have to enable the sources

check if the sources are active

system > administration > software sources

check them all

run

```
sudo apt-get update
```

and try again to install


you can also post the output from

```
cat /etc/apt/sources.list
```

ah, thank you. I apologise for my newbness.

---

### Post by jan quark on 2008-02-10
hey no problem
you are welcome
we are here to help mark the thread as solved pls
see signature

---

