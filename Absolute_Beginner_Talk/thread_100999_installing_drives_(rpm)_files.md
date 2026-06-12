---
title: "installing drives (rpm) files"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by Ted D. on 2005-12-08
Hi,
Re ubuntu 5.1
I have downloaded downloaded drivers for a canon i860 printer to the desktop. I have installed alien to convert them to deb. trouble is i am not sure what commands i am supposed put in. i have followed the routines provide at several postings without luck. the closest i have come to getting the right commands is a message can't find file. what commands do i put in to a) find the file  b)convert the drivers and c)install the drivers. There a two files one is the cups driver.
thanks for assistance in advance.
Ted D. Newbie to ubuntu an linux

---

### Post by ngnr on 2005-12-08
Hi, 

if the package is in your desktop type:

```

$ cd $HOME/Desktop

```

then:

```
$ sudo alien -i <packagename>.rpm
```

good luck :)

---

